---
title: İlk talep kullanan WCF Hizmetimi derleme
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: e6324087afa62f276766c733284dc69e425b89bc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425868"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>İlk talep kullanan WCF Hizmetimi derleme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WIF kullanarak talep kullanan WCF hizmetleri oluşturma senaryosu açıklanmaktadır. Talep kullanan web hizmeti senaryosunda genellikle üç katılımcı vardır: web hizmetinin kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS). Aşağıdaki şekilde bu senaryo anlatılmaktadır:  
  
 ![WIF temel talep kullanan WCF Hizmeti](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  WCF hizmeti istemcisi (bazen aracı olarak adlandırılır), STS'ye kimlik bilgilerini göndermek için WIF'yi kullanır ve başarılı bir kimlik doğrulamadan sonra aracıya STS tarafından bir belirteç verilir.  
  
2.  Aracı, bu STS tarafından verilen belirteci WCF hizmetine gönderir.  
  
3.  Talep kullanan WCF hizmeti, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır. Talep kullanan WCF hizmeti, belirteci uygulamak ve ayrıştırmak için WIF kullanır. Geliştiriciler uygun WIF API ve türleri gibi kullanın **ClaimsPrincipal** yetkilendirme gerçekleştirme gibi uygulamanın ihtiyaçları için.  
  
 .NET 4.5'ten başlayarak, WIF .NET Framework paketinin bir parçası olmuştur. WIF sınıflarının doğrudan çerçevede kullanılabilir olması tümleştirilmesini beyana dayalı kimliğin .NET taleplerin kullanılmasını kolaylaştırır, sağlar. WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur. WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.  
  
 STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir. Microsoft, iki sektör standardı STS sunar:  
  
-   [Active Directory Federasyon Hizmetleri (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure erişim denetimi hizmeti (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir. Azure Active Directory erişim denetimi (Access Control Service veya ACS olarak da bilinir), Microsoft Azure'nın bir parçası olarak sunulan bulut hizmetidir. Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz. Örneğin, bir parçası olan yerel geliştirme STS'si kullanabilirsiniz [kimlik ve erişim aracı Visual Studio için](https://go.microsoft.com/fwlink/?LinkID=245849) olduğu ücretsiz çevrimiçi.  
  
 WIF kullanarak ilk talep kullanan WCF hizmetinizi oluşturmak için bkz: [nasıl yapılır: WCF Web hizmeti uygulaması için WIF etkinleştirme](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Kullanmaya Başlama](../../../docs/framework/security/getting-started-with-wif.md)
