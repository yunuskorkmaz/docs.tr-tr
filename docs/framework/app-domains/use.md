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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674902"
---
# <a name="using-application-domains"></a>Uygulama Etki Alanlarını Kullanma
Uygulama etki alanı yalıtım ortak dil çalışma zamanı için bir birim sağlayın. Bunlar oluşturulur ve bir işlem içinde çalıştırın. Uygulama etki alanları genellikle Uygulama çalışma zamanını bir işleme yükleme ve bir uygulama etki alanındaki kullanıcı kodunun yürütülmesi için sorumlu olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur. Çalışma zamanı ana bilgisayarı, bir varsayılan uygulama etki alanı ve bir işlem oluşturur ve yönetilen kod içindeki çalıştırır. Çalışma zamanı ana bilgisayarları, ASP.NET, Microsoft Internet Explorer ve Windows Kabuğu'nu içerir.  
  
 Çoğu uygulama için kendi uygulama etki alanı oluşturma gerekmez; çalışma zamanı ana bilgisayarı tüm gerekli uygulama etki alanları oluşturulur. Ancak, oluşturabilir ve uygulamanızın kod yalıtmak için veya kullanın ve DLL'lerini Kaldır için gereken ek uygulama etki alanları yapılandırın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Bir uygulama etki alanı oluşturma](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Program aracılığıyla uygulama etki alanı oluşturmayı açıklar.  
  
 [Nasıl yapılır: Bir uygulama etki alanını boşaltma](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Program aracılığıyla uygulama etki alanını kaldırma işlemini açıklamaktadır.  
  
 [Nasıl yapılır: Bir uygulama etki alanını yapılandırma](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Uygulama etki alanı yapılandırma için bir giriş sağlar.  
  
 [Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Bir uygulama etki alanından kurulum bilgilerini alma açıklar.  
  
 [Nasıl yapılır: Uygulama etki alanına derlemeler yükleme](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Uygulama etki alanına bir derlemeyi yüklemek açıklar.  
  
 [Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Bir derleme hakkında bilgi almak nasıl açıklar.  
  
 [Gölge Kopyalama Bütünleştirilmiş Kodları](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Bunlar kullanımdayken nasıl gölge kopyalama derlemeleri güncelleştirmeler sağlar ve gölge kopyalama yapılandırma açıklanmaktadır.  
  
 [Nasıl yapılır: İlk fırsat özel durum bildirimleri alma](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Ortak dil çalışma zamanı için özel durum işleyicileri aramaya başlamadan önce bir özel durum, olarak oluşturuldu bir bildirim nasıl alabileceğiniz açıklanır.  
  
 [Bütünleştirilmiş Kod Yüklerini Çözme](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Kullanma hakkında yönergeler sağlar <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yükleme hataları çözmek için olay.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.AppDomain>  
 Uygulama etki alanını temsil eder. Oluşturma ve uygulama etki alanları denetlemek için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Derlemeler tarafından gerçekleştirilen işlevler genel bir bakış sağlar.  
  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.  
  
 [Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Dinamik derlemelerin nasıl oluşturulduğunu açıklar.  
  
 [Uygulama Etki Alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.  
  
 [Yansıma genel bakış](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.
