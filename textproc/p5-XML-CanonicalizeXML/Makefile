# Created by: Gea-Suan Lin <gslin@gslin.org>
# $FreeBSD$

PORTNAME=	XML-CanonicalizeXML
PORTVERSION=	0.05
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Extension for inclusive/exclusive canonicalization of XML

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

LIB_DEPENDS=	libxml2.so:textproc/libxml2

MAKE_JOBS_UNSAFE=	yes
USE_PERL5=	configure
USES=		perl5 tar:tgz

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/${SITE_ARCH_REL}/auto/XML/CanonicalizeXML/CanonicalizeXML.so

.include <bsd.port.mk>
