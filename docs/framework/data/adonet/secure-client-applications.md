---
title: Güvenli istemci uygulamaları
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: c8efdf4c4baceb22ee60bdcf333ad1fec9ebd2d0
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092715"
---
# <a name="secure-client-applications"></a>Güvenli istemci uygulamaları
Uygulamalar genellikle tüm veri kaybına neden veya aksi halde sistemden güvenlik açıklarına karşı korunması gereken birçok bölümü oluşur. Güvenli kullanıcı arabirimleri oluşturmak, birçok sorunu verileri veya sistem kaynaklarına erişebilmeniz için önce saldırganların engelleyerek engelleyebilirsiniz.  
  
## <a name="validate-user-input"></a>Kullanıcı girişini doğrulama  
 Verilere erişen bir uygulama oluştururken, tüm kabul Aksi halde kanıtlanmış kadar kötü amaçlı kullanıcı girişi. Bunun yapılmaması, uygulamanızı saldırılara açık bırakabilirsiniz. .NET Framework, bir etki alanına girilebilecek karakterlerin sayısını sınırlama gibi giriş denetimleri için değerleri zorla yardımcı olmak için sınıflar içerir. Olay kancaları değerleri geçerliliğini denetlemek için yordamlar yazmanıza olanak sağlar. Kullanıcı giriş verilerini doğrulanabilir ve bir uygulamanın maruz komut dosyası ve SQL ekleme kesin türü belirtilmiş, sınırlama yararlanan.  
  
> [!IMPORTANT]
>  Ayrıca, istemci uygulamasının olduğu gibi de veri kaynağında kullanıcı girişi doğrulamanız gerekir. Bir saldırgan, uygulamanızın aşmak ve veri kaynağına doğrudan saldırı tercih edebilirsiniz.  
  
 [Güvenlik ve Kullanıcı Girdisi](../../../../docs/standard/security/security-and-user-input.md)  
 Kullanıcı girişi içeren zarif ve potansiyel olarak tehlikeli olabilecek hataları nasıl ele alınacağını açıklar.  
  
 [ASP.NET Web sayfalarında kullanıcı girişini doğrulama](https://docs.microsoft.com/previous-versions/aspnet/7kh55542(v=vs.100))  
 ASP.NET doğrulama denetimleri kullanarak kullanıcı girişi doğrulama genel bakış.  
  
 [Windows Forms'ta Kullanıcı Girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fare ve klavye bir Windows Forms uygulaması'nda doğrulamak için bilgi ve bağlantılar sağlanmıştır.  
  
 [.NET framework normal ifadeleri](../../../../docs/standard/base-types/regular-expressions.md)  
 Nasıl kullanılacağını açıklar <xref:System.Text.RegularExpressions.Regex> kullanıcı girişi geçerliliğini denetlemek için sınıf.  
  
## <a name="windows-applications"></a>Windows uygulamaları  
 Geçmişte, Windows uygulamaları, genellikle tam izinlere sahip çalıştı. .NET Framework kod erişim güvenliği (CAS) kullanarak bir Windows uygulamasında kodu yürüten kısıtlamak için altyapı sağlar. Ancak, tek başına CA'lar uygulamanızı korumak yeterli değil.  
  
 [Windows Forms Güvenliği](../../../../docs/framework/winforms/windows-forms-security.md)  
 Windows Forms uygulamalarının güvenliğini nasıl açıklanır ve ilgili konulara bağlantılar sağlar.  
  
 [Windows Forms ve Yönetilmeyen Uygulamalar](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Bir Windows Forms uygulaması yönetilmeyen uygulamalarda etkileşim açıklar.  
  
 [Windows Forms için ClickOnce Dağıtımı](../../winforms/clickonce-deployment-for-windows-forms.md)  
 Nasıl kullanılacağını açıklar `ClickOnce` dağıtım bir Windows Forms uygulamasında ve güvenlikle ilgili etkileri anlatılmaktadır.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET ve XML Web Hizmetleri  
 ASP.NET uygulamaları genellikle bazı bölümlerini bir Web sitesi için erişimi kısıtlayabilir ve verileri koruma ve site güvenliği için başka mekanizmalar gerekir. Bu bağlantılar, ASP.NET uygulamanızın güvenliğini sağlamak için yararlı bilgiler sağlar.  
  
 XML Web hizmeti, bir ASP.NET uygulaması, bir Windows Forms uygulaması veya başka bir Web hizmeti tarafından tüketilen veri sağlar. Web hizmeti için güvenlik ve bunun yanı sıra istemci uygulaması için güvenlik yönetmeniz gerekmez.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[ASP.NET Web sitelerinin güvenliğini sağlama](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))|ASP.NET uygulamalarının güvenliğini nasıl ele alınmaktadır.|  
|[ASP.NET kullanılarak oluşturulan XML Web Hizmetleri güvenli hale getirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))|ASP.NET Web hizmeti için güvenlik uygulamak nasıl ele alınmaktadır.|  
|[Betik açıklara genel bakış](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Kötü amaçlı karakterler bir Web sayfasına eklemek için çalışır bir betik yararlanma saldırılara karşı koruma sağlamak nasıl ele alınmaktadır.|  
|[Web uygulamaları için temel güvenlik yöntemleri](https://docs.microsoft.com/previous-versions/aspnet/zdh19h94(v=vs.100))|Genel güvenlik bilgileri ve bağlantılar daha fazla tartışma için|  
  
## <a name="remoting"></a>Uzaktan iletişim  
 .NET uzaktan iletişim uygulama bileşenlerinin tümü tek bir bilgisayarda veya tüm dünya genelindeki dağılmış yaygın olarak dağıtılmış uygulamaları kolayca oluşturmanıza olanak sağlar. Diğer işlemlerde aynı bilgisayarda veya alt ağ üzerinden erişilebilen herhangi bir bilgisayarda nesneleri kullanan istemci uygulamalar oluşturabilirsiniz. .NET uzaktan iletişim, aynı işlemi diğer uygulama etki alanları ile iletişim kurmak için de kullanabilirsiniz.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uzak uygulama yapılandırması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))|Ortak sorunları önlemek için uzaktan iletişim uygulamalarını yapılandırmak nasıl ele alınmaktadır.|  
|[Uzaktan iletişim güvenlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))|Kimlik doğrulaması ve şifreleme hem de uzaktan iletişim için ilgili ek güvenlik konuları açıklanmaktadır.|  
|[Güvenlik ve uzaktan yönetim konuları](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Korumalı nesneler ve uygulama etki alanı kesişimi ile ilgili güvenlik konuları açıklanmaktadır.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Veri erişim stratejileri için öneriler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)
- [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
