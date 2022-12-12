PORTNAME= ex_ample
DISTVERSION= 0.1.0-pre202212120041
CATEGORIES= pattest
MAINTAINER= pat@patmaddox.com
COMMENT= A simple example Elixir application.
WWW= https://github.com/patmaddox/ex_ample

USES= pgsql:14+

USE_GITHUB= yes
GH_ACCOUNT= patmaddox
GH_TAGNAME= 9e66a81dc4c874dec62f162e902af5ef515455b3

ERLANG_VER?= 24
BUILD_DEPENDS= erlang-runtime${ERLANG_VER}>0:lang/erlang-runtime${ERLANG_VER} elixir-devel>0:lang/elixir-devel

MAKE_ENV+= PATH="${LOCALBASE}/lib/erlang${ERLANG_VER}/bin:${PATH}"

USE_LOCALE= en_US.UTF-8
MIX_ENV?= prod
.export MIX_ENV

USE_RC_SUBR= ex_ample
SUB_FILES= ex_ample.env.sample
PLIST_FILES= "@sample(,,0600) etc/ex_ample/ex_ample.env.sample"
PLIST_DIRS= etc/ex_ample

PLIST= ${WRKDIR}/PLIST
RELDIR= ${WRKSRC}/_build/${MIX_ENV}/rel/${PORTNAME}

# poudriere needs ALLOW_NETWORKING_PACKAGES="ex_ample"
# to permit hex / rebar / deps network requests
do-build:
	cd ${WRKSRC} && ${MAKE_ENV} mix local.hex --force && ${MAKE_ENV} mix local.rebar --force && ${MAKE_ENV} mix deps.get && ${MAKE_ENV} mix release
	cd ${RELDIR} && find . -name '*.bat' -delete
	cd ${RELDIR} && find . -name COOKIE -delete
	cd ${RELDIR} && find -s . -type f | sed -e 's/^\./libexec\/${PORTNAME}/' | tee ${PLIST}

do-install:
	cp -Rp ${RELDIR} ${STAGEDIR}${PREFIX}/libexec/
	mkdir ${STAGEDIR}${PREFIX}/etc/ex_ample
	cp ${WRKDIR}/ex_ample.env.sample ${STAGEDIR}${PREFIX}/etc/ex_ample/

.include <bsd.port.mk>
