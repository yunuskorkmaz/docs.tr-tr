---
title: Talep Kullanan İlk WCF Hizmetimi Derleme
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 330d785721cb434f74ec746310a71bfd39fefd0b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045550"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Talep Kullanan İlk WCF Hizmetimi Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WIF kullanarak talep kullanan WCF hizmetleri oluşturma senaryosu açıklanmaktadır. Talep kullanan web hizmeti senaryosunda genellikle üç katılımcı vardır: web hizmetinin kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS). Aşağıdaki şekilde bu senaryo anlatılmaktadır:  
  
 ![WıF temel talep kullanan WCF hizmeti bileşenlerini gösteren diyagram.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. WCF hizmeti istemcisi (bazen aracı olarak adlandırılır), STS'ye kimlik bilgilerini göndermek için WIF'yi kullanır ve başarılı bir kimlik doğrulamadan sonra aracıya STS tarafından bir belirteç verilir.  
  
2. Aracı, bu STS tarafından verilen belirteci WCF hizmetine gönderir.  
  
3. Talep kullanan WCF hizmeti, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır. Talep kullanan WCF hizmeti, belirteci uygulamak ve ayrıştırmak için WIF kullanır. Geliştiriciler, uygun WıF API ve türlerini kullanır, örneğin, uygulama için yetkilendirme uygulama gibi **ClaimsPrincipal** .  
  
 .NET 4,5 ' den başlayarak, WıF .NET Framework paketinin bir parçasıdır. WıF sınıflarının doğrudan çerçevede kullanılabilir olması, .NET 'teki talep tabanlı kimliğin daha ayrıntılı bir şekilde tümleştirilmesini sağlayarak taleplerin kullanılmasını kolaylaştırır. WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur. WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.  
  
 STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir. Microsoft, iki sektör standardı STS sunar:  
  
- [Active Directory Federasyon Hizmetleri (AD FS) (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir. Azure Active Directory Access Control (Access Control Service veya ACS olarak da bilinir), Microsoft Azure bir parçası olarak sunulan bir bulut hizmetidir. Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz. Örneğin, çevrimiçi olarak ücretsiz kullanıma sunulan [Visual Studio Için kimlik ve erişim aracının](https://go.microsoft.com/fwlink/?LinkID=245849) bir parçası olan yerel geliştirme sts 'sini kullanabilirsiniz.  
  
 WIF kullanarak ilk talep kullanan WCF hizmetinizi derlemek için bkz [. nasıl yapılır: WCF Web hizmeti uygulaması](how-to-enable-wif-for-a-wcf-web-service-application.md)için WIF 'yi etkinleştirin.
  
## <a name="see-also"></a>Ayrıca bkz.

- [WIF Kullanmaya Başlama](getting-started-with-wif.md)
