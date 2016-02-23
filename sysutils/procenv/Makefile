# Created by: James Hunt <jamesodhunt@ubuntu.com>
# $FreeBSD$

PORTNAME=	procenv
PORTVERSION=	0.44
CATEGORIES=	sysutils
MASTER_SITES=	https://github.com/jamesodhunt/procenv/archive/${PORTVERSION}.tar.gz#/procenv-${PORTVERSION}.tar.gz

MAINTAINER=	jamesodhunt@ubuntu.com
COMMENT=	Utility to show process environment

LICENSE=	GPLv3

BUILD_DEPENDS=	xmlwf:${PORTSDIR}/textproc/expat2

GNU_CONFIGURE=	yes
USES=		gmake
USE_AUTOTOOLS=	aclocal automake
USE_PERL5_BUILD=YES

FETCH_ARGS=	-Fpr

MAN1=		procenv.1

PLIST_FILES=	bin/procenv

NO_STAGE=	yes
.include <bsd.port.pre.mk>

.if ${OSVERSION} < 800505
BROKEN=		does not build on old ${OPSYS} versions
.endif

# Test to ensure procenv will actually run.
#
# This has the attractive side-effect of displaying the environment
# of the build system which may be of interest to those fixing FTBFS
# packages that build correctly locally.
regression-test: build
	@cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${GMAKE} check

test: regression-test

.include <bsd.port.post.mk>
