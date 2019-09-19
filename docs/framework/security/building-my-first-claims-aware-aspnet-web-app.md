---
title: Talep Kullanan İlk ASP.NET Web Uygulamamı Derleme
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 900ee49b4bf51eeb6e3b0c0cf6879cc12a0cb071
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045584"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Talep Kullanan İlk ASP.NET Web Uygulamamı Derleme
## <a name="applies-to"></a>Uygulanan Öğe  
  
- Windows Identity Foundation (WIF)  
  
- ASP.NET  
  
 Bu konuda, WIF kullanarak talep kullanan ASP.NET web uygulamaları oluşturma senaryosu açıklanmaktadır. Talep kullanan uygulama senaryosunda genellikle üç katılımcı vardır: uygulamanın kendisi, son kullanıcı ve Güvenlik Belirteci Hizmeti (STS). Aşağıdaki şekilde bu senaryo anlatılmaktadır:  
  
 ![WıF temel Web uygulaması bileşenlerini gösteren diyagram.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. Talep kullanan uygulama, kimliği doğrulanmamış istekleri tanımlamak ve bunları STS'ye yönlendirmek için WIF kullanır.  
  
2. Son kullanıcı, STS'ye kimlik bilgileri sağlar ve başarılı bir kimlik doğrulamadan sonra kullanıcıya STS tarafından belirteç verilir.  
  
3. Kullanıcı, istekte STS tarafından verilen belirteçle STS'den talep kullanan uygulamaya yönlendirilir.  
  
4. Talep kullanan uygulama, STS'ye ve verdiği belirteçlere güvenecek şekilde yapılandırılmıştır. Talep kullanan uygulama, belirteci doğrulamak ve ayrıştırmak için WIF kullanır. Geliştiriciler, uygun WıF API ve türlerini kullanır, örneğin, uygulama için yetkilendirme uygulama gibi **ClaimsPrincipal** .  
  
 .NET 4,5 ' den başlayarak, WıF .NET Framework paketinin bir parçasıdır. WıF sınıflarının doğrudan çerçevede kullanılabilir olması, .NET 'teki talep tabanlı kimliğin daha ayrıntılı bir şekilde tümleştirilmesini sağlayarak taleplerin kullanılmasını kolaylaştırır. WIF 4.5 ile, talep kullanan web uygulamaları geliştirmeye başlamak için bant dışı bileşenler yüklemenize gerek yoktur. WIF sınıfları artık çeşitli derlemeler arasında yayılmaktadır. Temel sınıflar System.Security.Claims, System.IdentityModel ve System.IdentityModel.Services'dır.  
  
 STS, başarılı kimlik doğrulamadan sonra belirteçler veren bir hizmettir. Microsoft, iki sektör standardı STS sunar:  
  
- [Active Directory Federasyon Hizmetleri (AD FS) (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 AD FS 2.0, Windows Server R2'nin bir parçasıdır ve şirket içi senaryolar için STS olarak kullanılabilir. ACS, Microsoft Azure platformunun bir parçası olarak sunulan bir bulut hizmetidir. Test ve eğitim amaçları için talep kullanan uygulamalar oluşturmak üzere başka STS'ler de kullanabilirsiniz. Örneğin, çevrimiçi olarak ücretsiz kullanıma sunulan [Visual Studio Için kimlik ve erişim aracının](https://go.microsoft.com/fwlink/?LinkID=245849) bir parçası olan yerel geliştirme sts 'sini kullanabilirsiniz.  
  
 WIF kullanarak ilk talep kullanan ASP.NET uygulamanızı oluşturmak için aşağıdakilerden birinde yer alan yönergeleri uygulayın:  
  
- [Nasıl yapılır: WıF kullanarak talep kullanan ASP.NET MVC web uygulaması oluşturma](how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [Nasıl yapılır: WıF kullanarak talep kullanan ASP.NET Web Forms uygulama oluşturma](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [Nasıl yapılır: Form tabanlı kimlik doğrulaması kullanarak talep kullanan ASP.NET uygulaması oluşturma](claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WIF Kullanmaya Başlama](getting-started-with-wif.md)
