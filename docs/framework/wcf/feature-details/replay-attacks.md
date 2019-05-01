---
title: Yeniden Yürütme Saldırıları
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: fefcb533cedb5405736ecda70c6879ebe00b8b49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991152"
---
# <a name="replay-attacks"></a>Yeniden Yürütme Saldırıları
A *tekrarlama saldırı* bir saldırgan, iki taraflar arasında iletileri akışını kopyalar ve bir veya daha fazla taraflar akışa başlayarak yeniden oynatılır oluşur. Saldırı bilgisayarların akış azaltılabilir sürece, sonuçta hatalı sonuçları, bir öğenin yedekli siparişler gibi çeşitli yasal iletileri olarak işleyin.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Bağlamaları yansıma saldırılarıyla karşılaşabilir  
 *Yansıma saldırıları* yanıt olarak alıcı geldiği gibi iletileri gönderen dön olumsuzlukları demektir. Standart *yeniden yürütme algılaması* Windows Communication Foundation (WCF) mekanizması otomatik olarak bu işlemez.  
  
 Yansıma saldırıları WCF service model imzalı ileti kimliği, istek iletilerini ekler ve bir imzalı bekliyor çünkü varsayılan olarak azaltılabilir `relates-to` üstbilgisi yanıt iletileri. Sonuç olarak, isteğine yanıt olarak yürütülemez. Güvenli, güvenilir, ileti (RM) senaryolarında, çünkü yansıma saldırıları azaltıldığından:  
  
- Oluşturma sırası yanıt iletisi şemaları ve Oluşturma sırası farklıdır.  
  
- İstemci bu türden iletilere anlayamıyor çünkü tek yönlü sıraları için istemcinin gönderdiği sırası iletileri yeniden yürütülemez.  
  
- Çift yönlü dizileri için iki sıranın kimlikleri benzersiz olmalıdır. Bu nedenle, bir giden dizisi iletisi (tüm dizisi üstbilgileri gövdeleri, çok oturum açtığınızı) geri gelen sırası iletiyi yürütülemez.  
  
 Yansıma saldırılarına yalnızca bağlamaları WS-Addressing olmadan olanlardır: simetrik anahtar tabanlı güvenliği kullanın-devre dışı WS Addressing ve özel bağlamalar. <xref:System.ServiceModel.BasicHttpBinding> Kullanılmıyor WS-Addressing varsayılan olarak yapar, ancak bunları simetrik anahtar tabanlı güvenlik, bu saldırısına açık olmasını sağlayan bir yolla kullanmaz.  
  
 Risk azaltma özel bağlamalar için güvenlik bağlamı kurmak değil veya WS-Addressing üst bilgileri gerektirecek şekilde kullanmaktır.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web grubu: Saldırgan olumsuzlukları isteği birden çok düğüm  
 Bir istemci, bir Web grubunda uygulanan bir hizmeti kullanır. Bir saldırganın bir düğüm grubunda gruptaki başka bir düğüme gönderilen bir istek başlayarak yeniden oynatılır. Hizmet yeniden başlatılırsa, ayrıca, yeniden yürütme önbellek, saldırganın isteği yeniden yürütme temizlenir. (Önbellek kullanılan, daha önce görülen ileti imzası değerlerini içerir ve bu nedenle bu imzaların yalnızca bir kez kullanılabilir olumsuzlukları önler. Yeniden yürütme önbellekler bir Web grubu arasında paylaşılmaz.)  
  
 Risk azaltma işlemleri şunlardır:  
  
- İleti modu güvenlik durum bilgisi olan güvenlik bağlamı belirteçleri (ile veya etkin güvenli konuşma olmadan) kullanın. Daha fazla bilgi için [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
- Hizmetini aktarım düzeyi güvenlik kullanacak şekilde yapılandırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
