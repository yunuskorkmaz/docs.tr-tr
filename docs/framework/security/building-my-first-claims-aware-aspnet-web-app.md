---
title: İlk talep kullanan ASP.NET Web uygulamamı derleme
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 76b02a0e6869b0d4de181b59296a0858aa80948c
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778162"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>İlk talep kullanan ASP.NET Web uygulamamı derleme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 Bu konuda, WIF kullanarak talep kullanan ASP.NET web uygulamaları oluşturma senaryosu açıklanmaktadır. Talep kullanan uygulama senaryosunda genellikle üç katılımcı vardır: uygulamanın kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS). Aşağıdaki şekilde bu senaryo anlatılmaktadır:  
  
 ![WIF temel Web uygulaması](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")  
  
1.  Talep kullanan uygulama, kimliği doğrulanmamış istekleri tanımlamak ve bunları STS'ye yönlendirmek için WIF kullanır.  
  
2.  Son kullanıcı, STS'ye kimlik bilgileri sağlar ve başarılı bir kimlik doğrulamadan sonra kullanıcıya STS tarafından belirteç verilir.  
  
3.  Kullanıcı, istekte STS tarafından verilen belirteçle STS'den talep kullanan uygulamaya yönlendirilir.  
  
4.  Talep kullanan uygulama, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır. Talep kullanan uygulama, belirteci doğrulamak ve ayrıştırmak için WIF kullanır. Geliştiriciler uygun WIF API ve türleri gibi kullanın **ClaimsPrincpal** yetkilendirme gerçekleştirme gibi uygulamanın ihtiyaçları için.  
  
 .NET 4.5'ten başlayarak, WIF .NET Framework paketinin bir parçası olmuştur. WIF sınıflarının doğrudan çerçevede kullanılabilir olması tümleştirilmesini beyana dayalı kimliğin .NET taleplerin kullanılmasını kolaylaştırır, sağlar. WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur. WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.  
  
 STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir. Microsoft, iki sektör standardı STS sunar:  
  
-   [Active Directory Federasyon Hizmetleri (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure erişim denetimi hizmeti (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir. ACS, Microsoft Azure platformunun bir parçası olarak sunulan bir bulut hizmetidir. Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz. Örneğin, bir parçası olan yerel geliştirme STS'si kullanabilirsiniz [kimlik ve erişim aracı Visual Studio için](https://go.microsoft.com/fwlink/?LinkID=245849) olduğu ücretsiz çevrimiçi.  
  
 WIF kullanarak ilk talep kullanan ASP.NET uygulamanızı oluşturmak için aşağıdakilerden birinde yer alan yönergeleri uygulayın:  
  
-   [Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET MVC Web Uygulaması Derleme](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Nasıl yapılır: WIF Kullanarak Talep Kullanan ASP.NET Web Forms Uygulaması Derleme](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Nasıl yapılır: Forms Tabanlı Kimlik Doğrulaması Kullanarak Talep Kullanan ASP.NET Uygulaması Derleme](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Kullanmaya Başlama](../../../docs/framework/security/getting-started-with-wif.md)
