---
title: "Uygulama Etki Alanlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53180d5d3d9314c3f078ddca8f5c155b01981f4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-domains"></a>Uygulama Etki Alanlarını Kullanma
Uygulama etki alanları yalıtım ortak dil çalışma zamanı için bir birim sağlayın. Bunlar oluşturulur ve bir işlem içinde çalıştırma. Uygulama etki alanları genellikle uygulamanın çalışma zamanı yükleme işlemi ve uygulama etki alanı içinde kullanıcı kodu yürütme sorumlu olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur. Çalışma zamanı ana bilgisayarı bir işlem ve bir varsayılan uygulama etki alanı oluşturur ve bunu içinde yönetilen kod çalıştırır. Çalışma zamanı ana bilgisayarlarını, ASP.NET, Microsoft Internet Explorer ve Windows Kabuğu'nu içerir.  
  
 Çoğu uygulama için kendi uygulama etki alanı oluşturma gerekmez; çalışma zamanı ana bilgisayar tüm gerekli uygulama etki alanları sizin için oluşturur. Ancak, oluşturabilir ve uygulamanızı kod ayırmak veya kullanın ve DLL'ler unload gerekiyorsa, ek uygulama etki alanlarını yapılandırın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: uygulama etki alanı oluşturma](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Program aracılığıyla uygulama etki alanı oluşturmayı açıklar.  
  
 [Nasıl yapılır: uygulama etki alanını boşaltma](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Program aracılığıyla bir uygulama etki alanını boşaltma açıklar.  
  
 [Nasıl yapılır: uygulama etki alanını yapılandırma](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Uygulama etki alanını yapılandırmak için bir giriş sağlar.  
  
 [Bir uygulama etki alanından kurulum bilgilerini alma](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Bir uygulama etki alanından kurulum bilgilerini almak açıklar.  
  
 [Nasıl yapılır: uygulama etki alanına derlemeler yükleme](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Uygulama etki alanına bir derlemeyi yüklemeye açıklar.  
  
 [Nasıl yapılır: bir derlemeden tür ve üye bilgilerini alın](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Derleme hakkında bilgi almak açıklar.  
  
 [Gölge kopyalama derlemeleri](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Bunlar kullanımdayken nasıl gölge kopyalama derlemeleri güncelleştirmeler sağlar ve gölge kopyalama yapılandırma açıklanmaktadır.  
  
 [Nasıl yapılır: ilk fırsat özel durum bildirimleri alma](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Ortak dil çalışma zamanı özel durum işleyicileri için arama başladıktan önce bir özel durum, olarak oluşturuldu bir bildirim nasıl alabileceğiniz açıklanmaktadır.  
  
 [Derleme yüklerini çözme](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Kullanma hakkında yönergeler sunmaktadır <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yükleme hataları gidermek için olay.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.AppDomain>  
 Uygulama etki alanını temsil eder. Oluşturma ve uygulama etki alanları denetleme yöntemleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ortak dil çalışma zamanı derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Derlemeleri tarafından gerçekleştirilen işlevler genel bir bakış sağlar.  
  
 [Derlemelerle programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.  
  
 [Dinamik yöntemleri ve derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Dinamik derlemelerin nasıl oluşturulduğunu açıklar.  
  
 [Uygulama etki alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.  
  
 [Yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.
