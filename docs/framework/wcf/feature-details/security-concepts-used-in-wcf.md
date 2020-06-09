---
title: WCF'de Kullanılan Güvenlik Kavramları
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: f852ba4e1100103289bc5fd879b19ebd40443b8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595186"
---
# <a name="security-concepts-used-in-wcf"></a>WCF'de Kullanılan Güvenlik Kavramları
Windows Communication Foundation (WCF) güvenliği, daha önce kullanılan ve çeşitli güvenlik altyapılarında dağıtılan kavramlar üzerine kurulmuştur.  
  
 WCF, HTTP (HTTPS) üzerinde Güvenli Yuva Katmanı (SSL) gibi bazı altyapıların bazılarını destekler. Ancak, WCF, SOAP kodlu iletiler üzerinden daha yeni birlikte çalışabilen güvenlik standartları (WS-Security gibi) uygulayarak mevcut güvenlik altyapılarını desteklemeye daha fazla yardımcı vardır. Mevcut mekanizmalar veya yeni birlikte çalışabilen standartlar kullanıyor olmanız durumunda, her ikisinin de her ikisi de aynı olan güvenlik kavramlarıdır. Mevcut altyapıların arkasındaki kavramları ve daha yeni standartları anlamak, bir uygulama için en iyi güvenlik modelini uygulamaya yönelik bir merkezidir.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web Hizmetleri güvenliğine giriş  

Microsoft düzenleri ve uygulamalar grubu, [WCF güvenlik kılavuzu](https://archive.codeplex.com/?p=wcfsecurityguide)adlı bir ayrıntılı teknik incelemeyi yazdı. Bu Teknik İnceleme, Web Hizmetleri, anahtar WCF güvenlik kavramları, intranet uygulama senaryoları ve Internet uygulaması senaryolarıyla bağlantılı olarak temel güvenlik kavramlarını açıklamaktadır.  
  
## <a name="industry-wide-security-specifications"></a>Sektör genelinde güvenlik belirtimleri  
  
### <a name="public-key-infrastructure"></a>Ortak anahtar altyapısı  

Ortak anahtar altyapısı (PKI), genel anahtar şifrelemesi kullanılarak elektronik bir işlemde yer alan her bir tarafı doğrulayan ve kimlik doğrulayan dijital sertifikalar, sertifika yetkilileri ve diğer kayıt yetkilileri sistemidir.
  
### <a name="kerberos-protocol"></a>Kerberos protokolü  
 *Kerberos protokolü* , bir Windows etki alanında kullanıcıların kimliğini doğrulayan bir güvenlik mekanizması oluşturmaya yönelik bir belirtimdir. Bir kullanıcının etki alanı içindeki diğer varlıklarla güvenli bir bağlam kurmasını sağlar. Windows 2000 ve üzeri platformlar Kerberos protokolünü varsayılan olarak kullanır. Sistem mekanizmalarını anlamak, intranet istemcilerle etkileşime girebilen bir hizmet oluştururken faydalıdır. Bunlara ek olarak, *Web Hizmetleri güvenliği Kerberos bağlama* yaygın olarak yayınlandığından, Internet istemcileriyle iletişim kurmak için Kerberos protokolünü kullanabilirsiniz (yani, Kerberos protokolü birlikte kullanılabilir). Windows 'da Kerberos protokolünün nasıl uygulandığı hakkında daha fazla bilgi için bkz. [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).  
  
### <a name="x509-certificates"></a>X. 509.440 sertifikaları  
 X. 509.440 sertifikaları, güvenlik uygulamalarında kullanılan birincil kimlik bilgileri biçimidir. X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/win32/seccertenroll/about-x-509-public-key-certificates). X. 509.440 sertifikaları bir sertifika deposunda depolanır. Windows çalıştıran bir bilgisayarda, her biri farklı bir amaca sahip birkaç tür sertifika deposu vardır. Farklı mağazalar hakkında daha fazla bilgi için bkz. [sertifika depoları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).  
  
## <a name="web-services-security-specifications"></a>Web Hizmetleri Güvenliği belirtimleri  
 Sistem tanımlı bağlamalar, yaygın olarak kullanılan birçok Web hizmeti güvenlik belirtimini destekler. Sistem tarafından sunulan bağlamaların tam listesi ve destekledikleri Web Hizmetleri belirtimleri için bkz: [sistem tarafından sunulan birlikte çalışabilirlik bağlamaları tarafından desteklenen Web Hizmetleri protokolleri](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları  
 WCF, bir hizmet veya işleme erişimi denetlemek için çeşitli yollar sağlar. Aralarında  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. ASP.NET üyelik sağlayıcısı  
  
3. ASP.NET rol sağlayıcısı  
  
4. Yetkilendirme Yöneticisi  
  
5. Kimlik modeli  
  
 Bu konular hakkında daha fazla bilgi için bkz. [Access Control mekanizmaları](access-control-mechanisms.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
