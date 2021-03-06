# Created by: Andrew Pantyukhin <infofarmer@FreeBSD.org>
# $FreeBSD$

PORTNAME=	griffith
PORTVERSION=	0.13
PORTREVISION=	6
CATEGORIES=	deskutils
MASTER_SITES=	http://launchpadlibrarian.net/87859599/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Lightweight film collection manager

LICENSE=	GPLv2+
LICENSE_FILE=	${WRKSRC}/COPYING

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}sqlite3>=0:databases/py-sqlite3 \
		${PYTHON_PKGNAMEPREFIX}sqlalchemy10>=0.5:databases/py-sqlalchemy10 \
		${PYTHON_PKGNAMEPREFIX}pillow>=0:graphics/py-pillow \
		${PYTHON_PKGNAMEPREFIX}reportlab1>=1.19:print/py-reportlab1

USES=		gmake gettext python:2 shebangfix tar:xz
SHEBANG_FILES=	griffith
USE_GNOME=	pygtk2
NO_BUILD=	yes
NO_ARCH=	yes

OPTIONS_DEFINE=		CHARDET LXML
OPTIONS_DEFAULT=	LXML

CHARDET_DESC=		chardet support
CHARDET_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}chardet>=0:textproc/py-chardet

LXML_DESC=		lxml support
LXML_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}lxml>=0:devel/py-lxml

post-patch:
.for file in Makefile
	@${REINPLACE_CMD} -e \
		'/^LANGUAGES=/s|find.*|cd i18n/\&\&ls -d *)|g ; \
		 /^PREFIX/s|?=|=|g ; s|/usr|${PREFIX}|; /ln -s/d; \
		 /^ETCDIR/s|=.*|= $$(PREFIX)/etc|g' ${WRKSRC}/${file}
.endfor
.for f in docs/en/Makefile docs/pl/Makefile docs/pt/Makefile
	@${REINPLACE_CMD} -e \
		'/^PREFIX/s|?=|=|g ; s|/usr|${PREFIX}|; \
		 /^MANDIR/s|=.*|=${STAGEDIR}${MANPREFIX}/man|g' \
		 ${WRKSRC}/${f}
.endfor

pre-install:
	${LN} -s ${DATADIR}/lib/${PORTNAME} ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
