PORTNAME= ex_ample
DISTVERSIONPREFIX= v
DISTVERSION= 0.1.0-8
DISTVERSIONSUFFIX= -g2956bcc
CATEGORIES= pattest
MAINTAINER= pat@patmaddox.com
COMMENT= A simple example Elixir application.

USE_GITHUB= yes
GH_ACCOUNT= patmaddox

ERLANG_VER?= 24
BUILD_DEPENDS= erlang-runtime${ERLANG_VER}>0:lang/erlang-runtime${ERLANG_VER} elixir-devel>0:lang/elixir-devel

MAKE_ENV+= PATH="${LOCALBASE}/lib/erlang${ERLANG_VER}/bin:${PATH}"

USE_LOCALE= en_US.UTF-8
MIX_ENV?= prod
.export MIX_ENV

# poudriere needs ALLOW_NETWORKING_PACKAGES="ex_ample"
# to permit hex / rebar / deps network requests
do-build:
	cd ${WRKSRC} && ${MAKE_ENV} mix local.hex --force && ${MAKE_ENV} mix local.rebar --force && ${MAKE_ENV} mix deps.get && ${MAKE_ENV} mix release

do-install:
	cd ${WRKSRC}/_build/${MIX_ENV}/rel/${PORTNAME} && ${COPYTREE_SHARE} . ${STAGEDIR}${PREFIX}/libexec/${PORTNAME}

.include <bsd.port.mk>
