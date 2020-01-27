---
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746421"
---
# <a name="securing-services-and-clients"></a>Hizmet ve İstemcileri Güvenli Hale Getirme
Bu bölümdeki bilgiler Windows Communication Foundation (WCF) ' deki programlama güvenliği ' ne odaklanır. Genellikle, bu, uygun bir sistem tarafından sağlanmış bağlamayı seçmeyi, Güvenlik öğesinin özelliklerini ayarlamayı ve ardından hizmet davranışlarının, kimlik bilgilerinin hizmet veya istemci tarafından kullanılmak üzere nasıl alındığını belirleyen özellikler ayarlanmasını içerir. Bu teknikler, [yaygın güvenlik senaryolarında](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)gösterildiği gibi çoğu senaryonun çoğu kullanıcının güvenlik gereksinimlerini kapsar. Senaryonuz daha fazla özellik gerektiriyorsa, önce [özel bağlamalarla güvenlik özelliklerine](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)bakın; bir çözüm görünmüyorsa bkz. [güvenliği genişletme](../../../../docs/framework/wcf/extending/extending-security.md). Zengin talepler kullanan bir sistem oluşturuyorsanız (veya ile birlikte çalışıyorsanız), [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)' de yer alan konulara bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 İletileri güvenli hale getirmek için kullanılan programlama modeline genel bakış.  
  
 [Aktarım Güvenliğine Genel Bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Aktarım katmanı üzerinden iletilerin güvenliğini sağlama konusuna genel bakış.  
  
 [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Windows Communication Foundation (WCF) ' de ileti düzeyi güvenliği kullanma nedenlerini özetler.  
  
 [Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Bir WCF oturumunun güvenliğini sağlarken gereken önemli noktalar hakkında bir tartışma.  
  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 X. 509.440 sertifikaları kullanılırken gereken bazı yaygın görevlerden oluşan bir açıklama.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Ortak Güvenlik Senaryoları](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [Güvenliği Genişletme](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
