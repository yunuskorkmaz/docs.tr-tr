---
title: Uygulama Etki Alanlarını Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: d6bbc2648608e9542158e0f281984174447633a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119733"
---
# <a name="using-application-domains"></a>Uygulama Etki Alanlarını Kullanma

Uygulama etki alanları, ortak dil çalışma zamanı için bir yalıtım birimi sağlar. Bunlar bir işlem içinde oluşturulup çalıştırılır. Uygulama etki alanları genellikle çalışma zamanının bir işleme yüklenmesi ve bir uygulama etki alanı içinde Kullanıcı kodu yürütmesi ile ilgili bir uygulama olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur. Çalışma zamanı ana bilgisayarı bir işlem ve varsayılan bir uygulama etki alanı oluşturur ve içinde yönetilen kodu çalıştırır. Çalışma zamanı Konakları ASP.NET, Microsoft Internet Explorer ve Windows kabuğu içerir.  
  
Çoğu uygulama için kendi uygulama etki alanınızı oluşturmanız gerekmez; çalışma zamanı ana bilgisayarı sizin için gerekli uygulama etki alanlarını oluşturur. Ancak, uygulamanızın kodu yalıtması veya dll 'Leri kullanması veya yüklemesi gerekiyorsa ek uygulama etki alanları oluşturabilir ve yapılandırabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  

[Nasıl yapılır: Uygulama Etki Alanı Oluşturma](how-to-create-an-application-domain.md)  
Programlı olarak bir uygulama etki alanı oluşturma işlemini açıklar.  
  
[Nasıl yapılır: Uygulama Etki Alanını Boşaltma](how-to-unload-an-application-domain.md)  
Bir uygulama etki alanını programlı olarak nasıl kaldırabileceğinizi açıklar.  
  
[Nasıl yapılır: Uygulama Etki Alanını Yapılandırma](how-to-configure-an-application-domain.md)  
Uygulama etki alanı yapılandırmaya bir giriş sağlar.  
  
[Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma](retrieve-setup-information.md)  
Bir uygulama etki alanından kurulum bilgilerinin nasıl alınacağını açıklar.  
  
[Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme](how-to-load-assemblies-into-an-application-domain.md)  
Bir derlemenin uygulama etki alanına nasıl yükleneceğini açıklar.  
  
[Nasıl yapılır: Bir Bütünleştirilmiş Koddan Tür ve Üye Bilgilerini Alma](../reflection-and-codedom/get-type-member-information.md)  
Bir derleme hakkında bilgilerin nasıl alınacağını açıklar.  
  
[Gölge Kopyalama Bütünleştirilmiş Kodları](shadow-copy-assemblies.md)  
Gölge kopyalamanın, kullanıldıkları sırada derlemeler için güncelleştirmelerin nasıl izin verdiğini ve gölge kopyalamayı nasıl yapılandıracağınızı açıklar.  
  
[Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma](how-to-receive-first-chance-exception-notifications.md)  
Ortak dil çalışma zamanı özel durum işleyicilerini aramaya başlamadan önce bir özel durumun oluşturulduğu bildirimini nasıl alacağınızı açıklar.  
  
[Bütünleştirilmiş Kod Yüklerini Çözme](../../standard/assembly/resolve-loads.md)  
Derleme yükleme başarısızlıklarını çözümlemek için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayının kullanılmasıyla ilgili rehberlik sağlar.  
  
## <a name="reference"></a>Başvuru  

<xref:System.AppDomain>  
Bir uygulama etki alanını temsil eder. Uygulama etki alanları oluşturmak ve denetlemek için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
Derlemeler tarafından gerçekleştirilen işlevlere genel bir bakış sağlar.  
  
[Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)  
Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.  
  
[Dinamik Yöntemleri ve Derlemeleri Yayma](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Dinamik derlemelerin nasıl oluşturulduğunu açıklar.  
  
[Uygulama Etki Alanları](application-domains.md)  
Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.  
  
[Yansımaya genel bakış](../reflection-and-codedom/reflection.md)  
Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.
