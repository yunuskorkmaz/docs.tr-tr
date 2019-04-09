---
title: WCF'de Kullanılan Güvenlik Kavramları
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: c995705e998ceee34ac9a3c2fc2343366f92ca00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142226"
---
# <a name="security-concepts-used-in-wcf"></a>WCF'de Kullanılan Güvenlik Kavramları
Windows Communication Foundation (WCF) güvenlik kavramları zaten kullanımda üzerine ve çeşitli güvenlik altyapısına içinde dağıtılmış.  
  
 WCF bu altyapılarının gibi Güvenli Yuva Katmanı (SSL) üzerinden HTTP (HTTPS) destekler. Ancak, WCF yeni birlikte çalışabilen güvenlik standartları (örneğin, WS-güvenlik) uygulayarak mevcut güvenlik altyapıları destekleme ötesinde SOAP kodlu iletileri gider. Mekanizmalar veya birlikte çalışabilen yeni standartları kullanarak olsun, hem de güvenlik kavramları aynıdır. Mevcut altyapıyla kavramları ve en yeni standartları anlama, uygulama için en iyi güvenlik modeli uygulamak için taşımaktadır.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web Hizmetleri için güvenliğine giriş  
 Microsoft Patterns and Practices grubu derinlemesine bir Teknik İnceleme burada indirme için kullanılabilir olan WCF Güvenlik Kılavuzu yazdı: [WCF Güvenlik Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=210210). Web Hizmetleri, anahtar WCF güvenlik kavramları, intranet uygulama senaryoları ve Internet uygulama senaryoları için ilgili olarak bu teknik incelemede, temel güvenlik kavramları açıklar.  
  
## <a name="industry-wide-security-specifications"></a>Endüstri genelinde güvenlik belirtimleri  
  
### <a name="public-key-infrastructure"></a>Ortak anahtar altyapısı  
 Ortak anahtar altyapısı (PKI), dijital sertifikalar, sertifika yetkililerini ve ortak anahtar şifrelemesi kullanarak elektronik bir işlemde katılan her iki taraf doğrulayan ve diğer yetkililerden sistemidir. Daha fazla bilgi için [Windows Server 2008 R2 sertifikası Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
 *Kerberos protokolü* bir güvenlik mekanizması oluşturduğunuz bir Windows etki alanındaki kullanıcıların kimlik doğrulaması için bir özelliğidir. Bu, bir etki alanındaki diğer varlıklarla güvenli bir bağlam'kurmak bir kullanıcı sağlar. Windows 2000 ve sonraki platformları varsayılan olarak Kerberos protokolünü kullanır. Bir hizmet oluşturma, intranet istemcilerle etkileşime gireceğini sisteminin mekanizmalarını anlama yararlı olur. Ayrıca, bu yana *Web Hizmetleri Güvenlik Kerberos bağlama* yaygın olan yayımlanan Internet istemcileri ile iletişim kurmak için Kerberos protokolünü kullanabilirsiniz (diğer bir deyişle, Kerberos protokolü birlikte). Kerberos protokolü Windows nasıl uygulandığı hakkında daha fazla bilgi için bkz. [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>X.509 sertifikaları  
 X.509 sertifikaları güvenlik uygulamalarında kullanılan birincil kimlik bilgisi bir biçimidir. X.509 hakkında daha fazla bilgi için bkz: sertifikaları [X.509 ortak anahtar sertifikaları](https://go.microsoft.com/fwlink/?LinkId=210213). X.509 sertifikaları bir sertifika deposunda depolanır. Windows çalıştıran bir bilgisayar sertifika depoları, her biri farklı bir amaca sahip çeşitli türlerde sahiptir. Farklı depoları hakkında daha fazla bilgi için bkz. [sertifika depolarını](https://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Güvenlik belirtimleri Web Hizmetleri  
 Sistem tarafından tanımlanan bağlamaları birçok yaygın olarak kullanılan web Hizmetleri güvenlik özelliklerini destekler. Sistem tarafından sağlanan bağlamalar ve web hizmetleri belirtimleri tam listesi için bkz: destekledikleri: [Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları  
 WCF hizmeti veya işlemi erişimi denetlemek için çeşitli yollarla sağlar. Bunlar arasında olan  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  ASP.NET üyelik sağlayıcısı  
  
3.  ASP.NET rol sağlayıcısını  
  
4.  Yetkilendirme Yöneticisi  
  
5.  Kimlik modeli  
  
 Bu konulara bakın hakkında daha fazla bilgi için [erişim denetimi mekanizmaları](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
