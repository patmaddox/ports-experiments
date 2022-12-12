PORTNAME= 1_simple
DISTVERSION= g202212111444
CATEGORIES= pattest
DISTFILES=
MAINTAINER= pat@patmaddox.com
COMMENT= A simple port that brings its own files.
WWW= https://github.com/patmaddox/ports-experiments/pattest/1_simple

NO_BUILD= yes
NO_INSTALL= yes
NO_TEST= yes

SUB_FILES= 1_simple another

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/1_simple ${STAGEDIR}${PREFIX}/bin
	${INSTALL_SCRIPT} ${WRKDIR}/another ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
