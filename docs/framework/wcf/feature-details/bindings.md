---
title: Windows Communication Foundation Bağlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e7071d56c8dc4b953c4b6349660ca4a8a1b7d23e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952624"
---
# <a name="windows-communication-foundation-bindings"></a>Windows Communication Foundation Bağlamaları
Windows Communication Foundation (WCF), bir uygulamanın yazılımının diğer yazılımlarla nasıl iletişim kurduğuna nasıl yazıldığını ayırır. Bağlamalar, istemcilerin ve hizmetlerin birbirleriyle iletişim kurması için gereken aktarım, kodlama ve protokol ayrıntılarını belirtmek için kullanılır. WCF, uç noktanın temel alınan tel temsilini oluşturmak için bağlamaları kullanır, bu nedenle bağlama ayrıntılarının çoğu, iletişim kuran taraflar tarafından üzerinde anlaşılmalıdır. Bunu başarmanın en kolay yolu, bir hizmetin istemcilerinin hizmet için uç noktanın kullandığı bağlamayı kullanması içindir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](../using-bindings-to-configure-services-and-clients.md).  
  
 Bağlama, bağlama öğeleri koleksiyonundan oluşur. Her öğe, uç noktanın istemcilerle nasıl iletişim kuracağını açıklar. Bağlama en az bir tane aktarım bağlama öğesi, en az bir ileti kodlama bağlama öğesi (taşıma bağlama öğesinin varsayılan olarak sağlayabileceği) ve diğer birçok protokol bağlama öğesini içermelidir. Bu açıklamanın dışında bir çalışma zamanı oluşturan işlem, her bağlama öğesinin bu çalışma zamanına kod katkıda bulunmasını sağlar.  
  
 WCF, bağlama öğelerinin ortak seçimlerini içeren bağlamalar sağlar. Bunlar, varsayılan ayarlarıyla kullanılabilir veya bu varsayılan değerleri kullanıcı gereksinimlerine göre değiştirebilirsiniz. Bu sistem tarafından sunulan bağlamalarda bağlama öğeleri ve bunların ayarları üzerinde doğrudan denetime izin veren özellikler vardır. Ayrıca bağlama 'nın her bir sürümünü kendi adı vererek, bir bağlamanın birden çok sürümüyle kolayca çalışabilirsiniz. Ayrıntılar için bkz. [sistem tarafından sunulan bağlamaları yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Bu sistem tarafından belirtilen bağlamalardan biri tarafından sağlanmayan bağlama öğeleri koleksiyonuna ihtiyacınız varsa, gereken bağlama öğeleri koleksiyonundan oluşan özel bir bağlama oluşturabilirsiniz. Bu özel bağlamaların oluşturulması ve yeni bir sınıf gerektirilmesi kolaydır, ancak bağlama öğelerini veya ayarlarını denetlemek için özellikler sağlamaz. Bağlama öğelerine erişebilir ve bunları içeren koleksiyon aracılığıyla ayarlarını değiştirebilirsiniz. Ayrıntılar için bkz. [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Yaygın senaryoları desteklemek için WCF 'nin sağladığı bağlamaları nasıl kullanacağınızı ve değiştirileceğini açıklar.  
  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 Kod içinde imperatively ve bildirimli olarak yapılandırma kullanarak hizmet ve istemciler için Windows Communication Foundation (WCF) bağlamalarının nasıl tanımlanacağını açıklar.  
  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Ne <xref:System.ServiceModel.Channels.CustomBinding> olduğunu ve ne zaman kullanıldığını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
