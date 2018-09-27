---
title: Güvenli istemci uygulamaları
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: a3b035d59a39ca20f6a81fbd40d39069a7cc43c2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397900"
---
# <a name="secure-client-applications"></a>Güvenli istemci uygulamaları
Uygulamalar genellikle tüm veri kaybına neden veya aksi halde sistemden güvenlik açıklarına karşı korunması gereken birçok bölümü oluşur. Güvenli kullanıcı arabirimleri oluşturmak, birçok sorunu verileri veya sistem kaynaklarına erişebilmeniz için önce saldırganların engelleyerek engelleyebilirsiniz.  
  
## <a name="validate-user-input"></a>Kullanıcı girişini doğrulama  
 Verilere erişen bir uygulama oluştururken, tüm kabul Aksi halde kanıtlanmış kadar kötü amaçlı kullanıcı girişi. Bunun yapılmaması, uygulamanızı saldırılara açık bırakabilirsiniz. .NET Framework, bir etki alanına girilebilecek karakterlerin sayısını sınırlama gibi giriş denetimleri için değerleri zorla yardımcı olmak için sınıflar içerir. Olay kancaları değerleri geçerliliğini denetlemek için yordamlar yazmanıza olanak sağlar. Kullanıcı giriş verilerini doğrulanabilir ve bir uygulamanın maruz komut dosyası ve SQL ekleme kesin türü belirtilmiş, sınırlama yararlanan.  
  
> [!IMPORTANT]
>  Ayrıca, istemci uygulamasının olduğu gibi de veri kaynağında kullanıcı girişi doğrulamanız gerekir. Bir saldırgan, uygulamanızın aşmak ve veri kaynağına doğrudan saldırı tercih edebilirsiniz.  
  
 [Güvenlik ve Kullanıcı Girdisi](../../../../docs/standard/security/security-and-user-input.md)  
 Kullanıcı girişi içeren zarif ve potansiyel olarak tehlikeli olabilecek hataları nasıl ele alınacağını açıklar.  
  
 [ASP.NET Web sayfalarında kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
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
  
 [ClickOnce dağıtımı için Windows Forms uygulamaları](https://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Nasıl kullanılacağını açıklar `ClickOnce` dağıtım bir Windows Forms uygulamasında ve güvenlikle ilgili etkileri anlatılmaktadır.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET ve XML Web Hizmetleri  
 ASP.NET uygulamaları genellikle bazı bölümlerini bir Web sitesi için erişimi kısıtlayabilir ve verileri koruma ve site güvenliği için başka mekanizmalar gerekir. Bu bağlantılar, ASP.NET uygulamanızın güvenliğini sağlamak için yararlı bilgiler sağlar.  
  
 XML Web hizmeti, bir ASP.NET uygulaması, bir Windows Forms uygulaması veya başka bir Web hizmeti tarafından tüketilen veri sağlar. Web hizmeti için güvenlik ve bunun yanı sıra istemci uygulaması için güvenlik yönetmeniz gerekmez.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[NIB: ASP.NET güvenlik](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|ASP.NET uygulamalarının güvenliğini nasıl ele alınmaktadır.|  
|[ASP.NET kullanılarak oluşturulan XML Web Hizmetleri güvenli hale getirme](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|ASP.NET Web hizmeti için güvenlik uygulamak nasıl ele alınmaktadır.|  
|[Betik açıklara genel bakış](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Kötü amaçlı karakterler bir Web sayfasına eklemek için çalışır bir betik yararlanma saldırılara karşı koruma sağlamak nasıl ele alınmaktadır.|  
|[ASP.NET Web uygulamaları için NIB: temel güvenlik uygulamaları](https://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|Genel güvenlik bilgileri ve bağlantılar daha fazla tartışma için|  
  
## <a name="remoting"></a>Uzaktan iletişim  
 .NET uzaktan iletişim uygulama bileşenlerinin tümü tek bir bilgisayarda veya tüm dünya genelindeki dağılmış yaygın olarak dağıtılmış uygulamaları kolayca oluşturmanıza olanak sağlar. Diğer işlemlerde aynı bilgisayarda veya alt ağ üzerinden erişilebilen herhangi bir bilgisayarda nesneleri kullanan istemci uygulamalar oluşturabilirsiniz. .NET uzaktan iletişim, aynı işlemi diğer uygulama etki alanları ile iletişim kurmak için de kullanabilirsiniz.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uzak uygulama yapılandırması](https://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|Ortak sorunları önlemek için uzaktan iletişim uygulamalarını yapılandırmak nasıl ele alınmaktadır.|  
|[Uzaktan iletişim güvenlik](https://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|Kimlik doğrulaması ve şifreleme hem de uzaktan iletişim için ilgili ek güvenlik konuları açıklanmaktadır.|  
|[Güvenlik ve uzaktan yönetim konuları](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Korumalı nesneler ve uygulama etki alanı kesişimi ile ilgili güvenlik konuları açıklanmaktadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Veri erişim stratejileri için öneriler](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
