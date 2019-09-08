---
title: Güvenli İstemci Uygulamaları
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: 15d2b2199344644392be0e9a530c046a77db8523
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794377"
---
# <a name="secure-client-applications"></a>Güvenli İstemci Uygulamaları
Uygulamalar genellikle, veri kaybına neden olabilecek veya sistemin güvenliğini tehlikeye atabilecek güvenlik açıklarına karşı korunması gereken pek çok bölümden oluşur. Güvenli kullanıcı arabirimleri oluşturmak, saldırganlar 'e veri veya sistem kaynaklarına erişmeden önce engelleyerek birçok sorunu önleyebilir.  
  
## <a name="validate-user-input"></a>Kullanıcı girişini doğrulama  
 Verilere erişen bir uygulama oluştururken, aksi takdirde Kullanıcı girişinin kötü amaçlı olduğundan emin olmanız gerekir. Bunun yapılmaması, uygulamanızı saldırılara karşı savunmasız bırakabilir. .NET Framework, girilen karakterlerin sayısını sınırlama gibi giriş denetimleri için bir değer etki alanı zorlamanıza yardımcı olacak sınıflar içerir. Olay kancaları, değerlerin geçerliliğini denetlemek için yordamlar yazmanızı sağlar. Kullanıcı girişi verileri doğrulanabilir ve kesin şekilde türlenebilir ve bir uygulamanın betiği ve SQL ekleme açıklarına maruz kalma olasılığını kısıtlar.  
  
> [!IMPORTANT]
> Ayrıca, istemci uygulamasındaki ve veri kaynağındaki Kullanıcı girişini de doğrulamanız gerekir. Saldırgan, uygulamanızı atlayıp doğrudan veri kaynağına saldırmayı tercih edebilir.  
  
 [Güvenlik ve Kullanıcı Girdisi](../../../standard/security/security-and-user-input.md)  
 Kullanıcı girişi ile ilgili hafif ve potansiyel olarak tehlikeli hataların nasıl işleneceğini açıklar.  
  
 [ASP.NET Web sayfalarında Kullanıcı girişini doğrulama](https://docs.microsoft.com/previous-versions/aspnet/7kh55542(v=vs.100))  
 ASP.NET doğrulama denetimlerini kullanarak Kullanıcı girişini doğrulamaya genel bakış.  
  
 [Windows Forms'ta Kullanıcı Girdisi](../../winforms/user-input-in-windows-forms.md)  
 Windows Forms uygulamasında fare ve klavye girişini doğrulamaya yönelik bağlantılar ve bilgiler sağlar.  
  
 [Normal Ifadeleri .NET Framework](../../../standard/base-types/regular-expressions.md)  
 Kullanıcı girişinin geçerliliğini denetlemek için <xref:System.Text.RegularExpressions.Regex> sınıfının nasıl kullanılacağını açıklar.  
  
## <a name="windows-applications"></a>Windows uygulamaları  
 Geçmişte Windows uygulamaları genellikle tam izinlerle çalışır. .NET Framework, kod erişim güvenliği (CAS) kullanarak bir Windows uygulamasında yürütülen kodu kısıtlamak için altyapıyı sağlar. Ancak, tek başına CA 'LAR uygulamanızı korumak için yeterli değildir.  
  
 [Windows Forms Güvenliği](../../winforms/windows-forms-security.md)  
 Windows Forms uygulamalarının güvenliğini nasıl sağladığını ve ilgili konuların bağlantılarını açıklar.  
  
 [Windows Forms ve Yönetilmeyen Uygulamalar](../../winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Windows Forms uygulamasındaki yönetilmeyen uygulamalarla nasıl etkileşim kuracağınızı açıklar.  
  
 [Windows Forms için ClickOnce Dağıtımı](../../winforms/clickonce-deployment-for-windows-forms.md)  
 Uygulamasının Windows Forms bir uygulamada `ClickOnce` nasıl kullanılacağını açıklar ve güvenlik etkilerine yönelik etkileri tartışır.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET ve XML Web Hizmetleri  
 ASP.NET uygulamalarının genellikle Web sitesinin bazı bölümlerine erişimi kısıtlanması ve veri koruma ve site güvenliği için diğer mekanizmalar sağlaması gerekir. Bu bağlantılar ASP.NET uygulamanızı güvenli hale getirmenin yararlı bilgilerini sağlar.  
  
 Bir XML Web hizmeti, bir ASP.NET uygulaması, Windows Forms uygulaması veya başka bir Web hizmeti tarafından tüketilen verileri sağlar. Web hizmetinin kendisi için güvenliği ve istemci uygulaması için güvenliği yönetmeniz gerekir.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[ASP.NET Web sitelerinin güvenliğini sağlama](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))|ASP.NET uygulamalarının nasıl güvenli hale alınacağını açıklar.|  
|[ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin güvenliğini sağlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))|Bir ASP.NET Web hizmeti için güvenliğin nasıl uygulanacağını açıklar.|  
|[Betikte kötüye bakış](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Bir Web sayfasına kötü amaçlı karakterler eklemeye yönelik bir komut dosyası yararlanma saldırılarına karşı nasıl koruma yapılacağını anlatır.|  
|[Web uygulamaları için temel güvenlik uygulamaları](https://docs.microsoft.com/previous-versions/aspnet/zdh19h94(v=vs.100))|Genel güvenlik bilgileri ve daha fazla tartışma bağlantıları,|  
  
## <a name="remoting"></a>Uzaktan iletişim  
 .NET uzaktan iletişim sayesinde, uygulama bileşenlerinin hepsi bir bilgisayarda olsun ya da dünyanın tamamında yayıldığında, yaygın olarak dağıtılmış uygulamalar oluşturmanıza olanak sağlar. Aynı bilgisayardaki veya ağ üzerinden erişilebilen diğer herhangi bir bilgisayarda bulunan diğer işlemlerde nesneleri kullanan istemci uygulamaları oluşturabilirsiniz. Aynı işlem içindeki diğer uygulama etki alanlarıyla iletişim kurmak için .NET uzaktan iletişimi de kullanabilirsiniz.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uzak uygulamaların yapılandırması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))|Yaygın sorunlardan kaçınmak için uzaktan iletişim uygulamalarının nasıl yapılandırılacağını açıklar.|  
|[Uzaktan Iletişim güvenliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))|Kimlik doğrulama ve şifrelemeyi ve uzaktan iletişim ile ilgili ek güvenlik konularını açıklar.|  
|[Güvenlik ve uzaktan Iletişim konuları](../../misc/security-and-remoting-considerations.md)|Korumalı nesneler ve uygulama etki alanı kesişen güvenlik sorunlarını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [Veri erişimi stratejileri için öneriler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)
- [Bağlantı Bilgilerini Koruma](protecting-connection-information.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
