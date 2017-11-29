---
title: "Güvenli istemci uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b42c06b9507894568a4299f23b62010e44076194
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="secure-client-applications"></a>Güvenli istemci uygulamaları
Uygulamalar genellikle tüm veri kaybına yol ya da aksi takdirde sistemi riske güvenlik açıklarından korunması gereken birçok bölümleri oluşur. Güvenli kullanıcı arabirimleri oluşturma, birçok sorunları saldırganlar veri veya sistem kaynakları erişebilmesi engelleyerek engelleyebilir.  
  
## <a name="validate-user-input"></a>Kullanıcı girişini doğrulama  
 Verilere erişen bir uygulama oluştururken, tüm varsayımında Aksi takdirde kanıtlanmış kadar kötü amaçlı kullanıcı girişi. Bunun Sağlanamaması, uygulama saldırılara karşı savunmasız bırakabilir. .NET Framework girilebilir karakter sayısını sınırlama gibi giriş denetimleri için değerlerin bir etki alanı zorunlu yardımcı olması için sınıflar içerir. Olay kancaları değerleri geçerliliğini denetlemek için yordamlar yazmanıza izin verin. Kullanıcı giriş verilerini doğrulanabilir ve kesin türü belirtilmiş, sınırlama uygulamanın maruz komut dosyası ve SQL ekleme yararlanan.  
  
> [!IMPORTANT]
>  Ayrıca, veri kaynağında de istemci uygulamasının olduğu gibi kullanıcı girişi doğrulamanız gerekir. Bir saldırgan, uygulamanızın atlayıp doğrudan veri kaynağına saldırı vermesini tercih edebilirsiniz.  
  
 [Güvenlik ve kullanıcı girişi](../../../../docs/standard/security/security-and-user-input.md)  
 Kullanıcı girişi içeren zarif ve potansiyel olarak tehlikeli olabilecek hataların nasıl ele alınacağını açıklar.  
  
 [ASP.NET Web sayfaları kullanıcı girişini doğrulama](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 ASP.NET doğrulama denetimleri kullanan kullanıcı girişi doğrulama genel bakış.  
  
 [Windows Forms uygulamasında kullanıcı girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fare ve bir Windows Forms uygulamasında klavye doğrulama için bilgi ve bağlantılar sağlanmıştır.  
  
 [.NET framework normal ifadeleri](../../../../docs/standard/base-types/regular-expressions.md)  
 Nasıl kullanılacağını açıklar <xref:System.Text.RegularExpressions.Regex> kullanıcı girişi geçerliliğini denetlemek için sınıf.  
  
## <a name="windows-applications"></a>Windows uygulamaları  
 Geçmişte, Windows uygulamaları genellikle tam izinleri olan verdi. .NET Framework kod erişim güvenliği (CAS) kullanarak bir Windows uygulaması'nda kod yürütmek kısıtlamak için altyapı sağlar. Ancak, tek başına CA'lar, uygulamanızın korumak yeterli değil.  
  
 [Windows Forms güvenliği](../../../../docs/framework/winforms/windows-forms-security.md)  
 Windows Forms uygulamalarının güvenliğini sağlama açıklanır ve ilgili konulara bağlantılar sağlar.  
  
 [Windows Forms ve yönetilmeyen uygulamalar](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Bir Windows Forms uygulaması yönetilmeyen uygulamalarda etkileşimde açıklar.  
  
 [ClickOnce dağıtımı Windows Forms uygulamaları](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Nasıl kullanılacağını açıklar `ClickOnce` dağıtım bir Windows Forms uygulamasında ve güvenlik uygulamalarını açıklar.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET ve XML Web Hizmetleri  
 ASP.NET uygulamaları genellikle Web sitesi bazı kısımları erişimi kısıtlayabilir ve verileri koruma ve site güvenliği için diğer mekanizmalar gerekir. Bu bağlantılar ASP.NET uygulamanızın güvenliğini sağlamak için yararlı bilgiler sağlar.  
  
 XML Web hizmeti, bir ASP.NET uygulaması, bir Windows Forms uygulaması veya başka bir Web hizmeti tarafından tüketilen veri sağlar. Web hizmeti için güvenlik ve bunun yanı sıra istemci uygulaması için güvenlik yönetmesi gerekir.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[NIB: ASP.NET güvenliği](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)|ASP.NET uygulamalarının güvenliğini sağlama anlatılmaktadır.|  
|[ASP.NET kullanılarak oluşturulan XML Web Hizmetleri güvenli hale getirme](http://msdn.microsoft.com/en-us/354b2ab1-2782-4542-b32a-dc560178b90c)|ASP.NET Web hizmeti için güvenlik uygulamak nasıl ele alınmaktadır.|  
|[Komut dosyası açıkları genel bakış](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Bir Web sayfasına amaçlı karakter eklemesini çalışır bir komut dosyası yararlanma saldırılara karşı koruma sağlamak nasıl ele alınmaktadır.|  
|[ASP.NET Web uygulamaları için NIB: temel güvenlik uygulamaları](http://msdn.microsoft.com/en-us/94a52ab8-731d-417e-b997-721baf43df38)|Genel güvenlik bilgileri ve bağlantıları daha fazla bilgi için|  
  
## <a name="remoting"></a>Uzaktan iletişim  
 .NET uzaktan iletişim uygulama bileşenlerinin tümünü tek bir bilgisayar üzerinde veya tüm dünyadaki dağılmış yaygın olarak dağıtılan uygulamaları kolayca oluşturmanıza olanak sağlar. Diğer işlemlerinde aynı bilgisayarda veya kendi ağ üzerinden erişilebilen herhangi bir bilgisayarda nesneleri kullanan istemci uygulamaları oluşturabilirsiniz. .NET uzaktan iletişim, diğer uygulama etki alanları aynı işlemde ile iletişim kurmak için de kullanabilirsiniz.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uzak uygulama yapılandırması](http://msdn.microsoft.com/en-us/92c0c097-d984-4315-835b-7490ecdf1097)|Sık karşılaşılan sorunları önlemek için uzaktan iletişim uygulamalarının nasıl yapılandırılacağını açıklar.|  
|[Uzaktan iletişim güvenliği](http://msdn.microsoft.com/en-us/9574262c-d4b1-41c5-8600-24ff147c0add)|Uzaktan iletişim için ilgili ek güvenlik konuları yanı sıra kimlik doğrulama ve şifreleme açıklar.|  
|[Güvenlik ve uzaktan yönetim konuları](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Korumalı nesneler ve uygulama etki alanı aşma ile ilgili güvenlik sorunları açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Veri erişim stratejileri için öneriler](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Uygulamalarının güvenliğini sağlama](/visualstudio/ide/securing-applications)  
 [Bağlantı bilgileri koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
