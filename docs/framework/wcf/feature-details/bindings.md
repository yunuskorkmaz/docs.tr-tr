---
title: Windows Communication Foundation Bağlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e69cd500c50e9d76824d0e438a1af86f3a722c52
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848042"
---
# <a name="windows-communication-foundation-bindings"></a>Windows Communication Foundation Bağlamaları
Windows Communication Foundation (WCF) nasıl, diğer yazılımlarla iletişim kurduğu gelen uygulama yazılımı nasıl yazılır ayırır. Bağlamaları, taşıma, kodlama ve istemciler ve hizmetler birbirleri ile iletişim kurmak için gerekli Protokolü ayrıntıları belirtmek için kullanılır. WCF bağlamaları bağlama ayrıntıları çoğunu iletişim kuran taraflarca varılmış gerekir böylece temel alınan hat gösterimine uç noktası oluşturmak için kullanır. Bunu yapmanın en kolay yolu, bir hizmet bağlaması aynı hizmet kullanımıyla ilgili uç noktayı kullanmak istemcileri içindir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](~/docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
 Bir bağlama bağlama öğelerinin bir koleksiyonunu oluşur. Her öğe endpoint istemcilerin ile nasıl iletişim kurar, bazı yönleri açıklanmaktadır. Bir bağlamanın en az bir aktarım bağlama öğesi, (varsayılan olarak Aktarım bağlama öğesinin sağlayabilirsiniz) en az bir ileti kodlama bağlama öğesi içermelidir ve diğer herhangi bir sayıda protokol bağlama öğeleri. İşlemin, bu açıklama dışında bir çalışma zamanı derlemeleri her bağlama öğesi, kod, çalışma zamanı katkıda bulunmasına izin verir.  
  
 WCF bağlama öğelerinin ortak seçimleri içeren bağlamalarını sunar. Bunlar, varsayılan ayarlarla kullanılabilir veya kullanıcı gereksinimlerine göre bu varsayılan değerleri değiştirebilirsiniz. Bu sistem tarafından sağlanan bağlamaları bağlama öğeleri ve ayarları üzerinde doğrudan denetim sağlayan özelliklere sahiptir. Her sürüm bağlama vererek yan yana bir bağlamanın birden çok sürümünün olduğu da bir kolayca çalışabilirsiniz kendi adı. Ayrıntılar için bkz [Configuring System-Provided bağlamaları](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Koleksiyonu gerekiyorsa bağlama öğeleri sağlanmadığından bu sistem tarafından sağlanan bağlamaları biri tarafından bağlama gerekli öğelerinin koleksiyonunu içeren özel bir bağlama oluşturabilirsiniz. Bu özel bağlamalar oluşturma yapmak kolaydır ve yeni bir sınıf olması, ancak bunlar özellikleri bağlama öğeleri veya ayarlarını denetlemek için sağlamaz. Bağlama öğeleri erişebilir ve bunları içeren koleksiyonu aracılığıyla ayarlarını değiştirin. Ayrıntılar için bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Yaygın senaryoları desteklemek için WCF sağlayan bağlamaları değiştirmek ve nasıl kullanılacağını açıklar.  
  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 Windows Communication Foundation (WCF) hizmet ve istemcileri bağlamalarda kesin kod ve yapılandırma bildirimli olarak kullanarak nasıl tanımlanacağını açıklar.  
  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Ne açıklayan bir <xref:System.ServiceModel.Channels.CustomBinding> olduğunu ve bunu ne zaman kullanılır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
