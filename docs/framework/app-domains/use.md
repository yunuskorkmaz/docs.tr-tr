---
title: Uygulama Etki Alanlarını Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674902"
---
# <a name="using-application-domains"></a>Uygulama Etki Alanlarını Kullanma
Uygulama etki alanları, ortak dil çalışma zamanı için bir yalıtım birimi sağlar. Bunlar bir işlem içinde oluşturulup çalıştırılır. Uygulama etki alanları genellikle çalışma zamanının bir işleme yüklenmesi ve bir uygulama etki alanı içinde Kullanıcı kodu yürütmesi ile ilgili bir uygulama olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur. Çalışma zamanı ana bilgisayarı bir işlem ve varsayılan bir uygulama etki alanı oluşturur ve içinde yönetilen kodu çalıştırır. Çalışma zamanı Konakları ASP.NET, Microsoft Internet Explorer ve Windows kabuğu içerir.  
  
 Çoğu uygulama için kendi uygulama etki alanınızı oluşturmanız gerekmez; çalışma zamanı ana bilgisayarı sizin için gerekli uygulama etki alanlarını oluşturur. Ancak, uygulamanızın kodu yalıtması veya dll 'Leri kullanması veya yüklemesi gerekiyorsa ek uygulama etki alanları oluşturabilir ve yapılandırabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Uygulama etki alanı oluşturma](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Programlı olarak bir uygulama etki alanı oluşturma işlemini açıklar.  
  
 [Nasıl yapılır: Uygulama etki alanını kaldırma](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Bir uygulama etki alanını programlı olarak nasıl kaldırabileceğinizi açıklar.  
  
 [Nasıl yapılır: Uygulama etki alanı yapılandırma](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Uygulama etki alanı yapılandırmaya bir giriş sağlar.  
  
 [Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Bir uygulama etki alanından kurulum bilgilerinin nasıl alınacağını açıklar.  
  
 [Nasıl yapılır: Derlemeleri bir uygulama etki alanına yükleme](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Bir derlemenin uygulama etki alanına nasıl yükleneceğini açıklar.  
  
 [Nasıl yapılır: Bir derlemeden tür ve üye bilgilerini alma](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Bir derleme hakkında bilgilerin nasıl alınacağını açıklar.  
  
 [Gölge Kopyalama Bütünleştirilmiş Kodları](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Gölge kopyalamanın, kullanıldıkları sırada derlemeler için güncelleştirmelerin nasıl izin verdiğini ve gölge kopyalamayı nasıl yapılandıracağınızı açıklar.  
  
 [Nasıl yapılır: Birinci şans özel durum bildirimlerini al](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Ortak dil çalışma zamanı özel durum işleyicilerini aramaya başlamadan önce bir özel durumun oluşturulduğu bildirimini nasıl alacağınızı açıklar.  
  
 [Bütünleştirilmiş Kod Yüklerini Çözme](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Derleme yükleme başarısızlıklarını çözümlemek için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı kullanma hakkında rehberlik sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.AppDomain>  
 Bir uygulama etki alanını temsil eder. Uygulama etki alanları oluşturmak ve denetlemek için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Derlemeler tarafından gerçekleştirilen işlevlere genel bir bakış sağlar.  
  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.  
  
 [Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Dinamik derlemelerin nasıl oluşturulduğunu açıklar.  
  
 [Uygulama Etki Alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.  
  
 [Yansımaya genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.
