# $FreeBSD$

PORTNAME=	ksysguardd
PORTVERSION=	${KDE4_WORKSPACE_VERSION}
CATEGORIES=	sysutils kde
MASTER_SITES=	KDE/${KDE4_APPLICATIONS_BRANCH}/applications/${KDE4_APPLICATIONS_VERSION}/src
DISTNAME=	kde-workspace-${PORTVERSION}
DIST_SUBDIR=	KDE/${PORTVERSION}

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KDE System Guard Daemon

DISTINFO_FILE=	${.CURDIR:H:H}/x11/kde4-workspace/distinfo
USES=		cmake kde:4 tar:xz
CMAKE_ARGS+=	-DBIN_INSTALL_DIR:STRING="${PREFIX}/bin" \
		-DSYSCONF_INSTALL_DIR:STRING="${PREFIX}/etc"

EXTRACT_AFTER_ARGS=	'${DISTNAME}/ksysguard/${PORTNAME}' \
			'${DISTNAME}/ksysguard/example/${PORTNAME}rc' \
			'${DISTNAME}/ksysguard/gui/SignalIDs.h'

WRKSRC=		${WRKDIR}/${DISTNAME}/ksysguard/${PORTNAME}

PLIST_FILES=	bin/${PORTNAME} \
		etc/${PORTNAME}rc

pre-build:
	${REINPLACE_CMD} -e 's/<config-workspace.h>/"config-${PORTNAME}.h"/' \
		${WRKSRC}/${PORTNAME}.c

.include <bsd.port.mk>
