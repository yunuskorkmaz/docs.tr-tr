---
title: Hizmet ve İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 713737b129771967958fddf44e9ef28583d49422
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554084"
---
# <a name="securing-services-and-clients"></a>Hizmet ve İstemcileri Güvenli Hale Getirme
Bu bölümdeki bilgiler Windows Communication Foundation (WCF) ' deki programlama güvenliği ' ne odaklanır. Genellikle, bu, uygun bir sistem tarafından sağlanmış bağlamayı seçmeyi, Güvenlik öğesinin özelliklerini ayarlamayı ve ardından hizmet davranışlarının, kimlik bilgilerinin hizmet veya istemci tarafından kullanılmak üzere nasıl alındığını belirleyen özellikler ayarlanmasını içerir. Bu teknikler, [yaygın güvenlik senaryolarında](common-security-scenarios.md)gösterildiği gibi çoğu senaryonun çoğu kullanıcının güvenlik gereksinimlerini kapsar. Senaryonuz daha fazla özellik gerektiriyorsa, önce [özel bağlamalarla güvenlik özelliklerine](security-capabilities-with-custom-bindings.md)bakın; bir çözüm görünmüyorsa bkz. [güvenliği genişletme](../extending/extending-security.md). Zengin talepler kullanan bir sistem oluşturuyorsanız (veya ile birlikte çalışıyorsanız), [Yetkilendirme](authorization-in-wcf.md)' de yer alan konulara bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [WCF Güvenliğini Programlama](programming-wcf-security.md)  
 İletileri güvenli hale getirmek için kullanılan programlama modeline genel bakış.  
  
 [Taşıma Güvenliği Genel Bakış](transport-security-overview.md)  
 Aktarım katmanı üzerinden iletilerin güvenliğini sağlama konusuna genel bakış.  
  
 [İleti Güvenliği](message-security-in-wcf.md)  
 Windows Communication Foundation (WCF) ' de ileti düzeyi güvenliği kullanma nedenlerini özetler.  
  
 [Güvenli Oturumlar](secure-sessions.md)  
 Bir WCF oturumunun güvenliğini sağlarken gereken önemli noktalar hakkında bir tartışma.  
  
 [Sertifikalarla Çalışma](working-with-certificates.md)  
 X. 509.440 sertifikaları kullanılırken gereken bazı yaygın görevlerden oluşan bir açıklama.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik Kavramları](security-concepts.md)  
  
 [Güvenliği Genişletme](../extending/extending-security.md)  
  
 [Ortak Güvenlik Senaryoları](common-security-scenarios.md)  
  
 [Bağlamalar ve Güvenlik](bindings-and-security.md)  
  
 [Özel Bağlamalarla Güvenlik Özellikleri](security-capabilities-with-custom-bindings.md)  
  
 [Güvenliği Genişletme](../extending/extending-security.md)  
  
 [Yetkilendirme](authorization-in-wcf.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../basic-wcf-programming.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
