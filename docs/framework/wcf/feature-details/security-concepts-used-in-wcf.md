---
title: "WCF'de Kullanılan Güvenlik Kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0f490fc09ada9ee80cb6cee12e9e9061e820026e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-concepts-used-in-wcf"></a>WCF'de Kullanılan Güvenlik Kavramları
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Güvenlik temel kavramları kullanılmakta olan yerleşik ve çeşitli güvenlik altyapılar içinde dağıtılır.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bazı Bu altyapılar gibi Güvenli Yuva Katmanı (SSL) üzerinden HTTP (HTTPS) destekler. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeni birlikte çalışabilir güvenliği standartları'nı (örneğin, WS-güvenlik) uygulayarak mevcut güvenlik altyapıları destekleme ötesinde SOAP kodlanmış iletileri üzerinden gider. Yeni birlikte çalışabilir standartlar veya varolan mekanizmaları kullanıp kullanmadığınızı güvenlik kavramları her ikisi de aynıdır. Varolan altyapıları kavramları ve daha yeni standartları anlama, uygulama için en iyi güvenlik modeli uygulamak için taşımaktadır.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web Hizmetleri için güvenlik giriş  
 Microsoft Patterns and Practices grubu buraya indirme için kullanılabilir olan WCF güvenlik kılavuzu üzerinde ayrıntılı teknik incelemesi yazdı: [WCF Güvenlik Kılavuzu'nu](http://go.microsoft.com/fwlink/?LinkId=210210). Web Hizmetleri, anahtar WCF güvenlik kavramları, intranet uygulama senaryoları ve Internet uygulama senaryoları için ilgili olarak bu teknik temel güvenlik kavramları açıklar.  
  
## <a name="industry-wide-security-specifications"></a>Sektör çapında güvenlik özellikleri  
  
### <a name="public-key-infrastructure"></a>Ortak anahtar altyapısı  
 Ortak anahtar altyapısı (PKI), dijital sertifikalar, sertifika yetkilileri ve ortak anahtar şifrelemesi kullanılarak elektronik bir işlemde her taraf doğrulayan ve diğer yetkililerden için kullanılan bir sistemdir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Server 2008 R2 Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
 *Kerberos protokolü* bir Windows etki alanındaki kullanıcıların kimliğini doğrulayan bir güvenlik mekanizması oluşturma için belirtimidir. Kullanıcının bir etki alanındaki diğer varlıklarla güvenli bir bağlam kurmak izin verir. Windows 2000 ve üstü platformları varsayılan Kerberos protokolünü kullanır. Bir hizmet oluşturma intranet istemcileri ile etkileşime gireceğini sistem mekanizmalarını anlama yararlıdır. Ayrıca, bu yana *Web Hizmetleri Güvenlik Kerberos bağlama* yaygın olan yayımlanan, Internet istemcileri ile iletişim kurmak için Kerberos protokolünü kullanabilirsiniz (diğer bir deyişle, Kerberos protokolü birlikte çalışabilir). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Kerberos protokolünün Windows'da uygulanır bkz [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>X.509 sertifikaları  
 X.509 sertifikaları güvenlik uygulamalarında kullanılan birincil kimlik bilgisi şeklindedir. X.509 hakkında daha fazla bilgi için bkz: sertifikalar [X.509 ortak anahtar sertifikaları](http://go.microsoft.com/fwlink/?LinkId=210213). X.509 sertifikaları bir sertifika deposunda saklanır. Windows çalıştıran bir bilgisayarı sertifika depoları, her biri farklı bir amaç çeşitli türlerde vardır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]farklı depoları bkz [sertifika depolarını](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Güvenlik özellikleri Web Hizmetleri  
 Sistem tarafından tanımlanan bağlamaları birçok yaygın olarak kullanılan web Hizmetleri güvenlik özelliklerini destekler. Sistem tarafından sağlanan bağlamalar ve web hizmetleri belirtimleri tam listesi için bkz: destekledikleri: [Web Hizmetleri protokolleri desteklenen System-Provided birlikte kullanılabilirlik bağlamaları ile](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları  
 WCF bir hizmet veya işlemi erişimi denetlemek için çeşitli yöntemler sağlar. Bunlar arasında olan  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  ASP.NET üyelik sağlayıcısı  
  
3.  ASP.NET rol sağlayıcısı  
  
4.  Yetkilendirme Yöneticisi  
  
5.  Kimlik modeli  
  
 Bu konular bakın hakkında daha fazla bilgi için [erişim denetimi mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
