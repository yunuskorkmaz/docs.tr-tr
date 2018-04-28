---
title: Yeniden Yürütme Saldırıları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e827c51378b9f75835b9b98280b4995d2cae2fc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="replay-attacks"></a>Yeniden Yürütme Saldırıları
A *tekrarlama saldırı* bir saldırgan, iki taraf arasında ileti akışı kopyalar ve bir veya daha fazla tarafların akışa başlayarak yeniden oynatılır oluşur. Azaltıldığından sürece, bilgisayarlar saldırı tabi akış yasal iletileri, bir öğenin yedekli siparişleri gibi hatalı sonuçları aralığında kaynaklanan olarak işler.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Yansıma saldırılarına maruz bağlamaları olabilir  
 *Yansıma saldırıları* alıcısı yanıt olarak geldiği gibi iletileri gönderen dön yürütmelerini demektir. Standart *yeniden yürütme algılaması* içinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mekanizması otomatik olarak işlemiyor bu.  
  
 Yansıma saldırıları için varsayılan olarak azaltıldığından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet modeli imzalı ileti kimliği istek iletilerini ekler ve bir imzalı bekliyor `relates-to` üstbilgisi yanıt iletileri. Sonuç olarak, isteğine yanıt olarak yeniden olamaz. Güvenli güvenilir ileti (RM) senaryolarında yansıma saldırıları çünkü azaltıldığından:  
  
-   Oluşturma sırası ve Oluşturma sırası yanıt iletisi şemaları farklıdır.  
  
-   İstemci bu türden iletilere anlayamıyor çünkü tek yönlü sıraları için istemci gönderir sırası iletilerinin yeniden yeniden yürütülmesi olamaz.  
  
-   Çift yönlü sıraları için iki sırası kimliklerinin benzersiz olması gerekir. Bu nedenle, bir giden sırası iletisi (tüm dizisi üstbilgi ve gövdelerini, çok imzalanmış) geri gelen sırası iletisi yeniden olamaz.  
  
 Yansıma saldırılarına yalnızca bağlamaları WS adresleme olmadan olanlardır: WS adresleme-devre dışı olması ve simetrik anahtar tabanlı güvenlik kullanan özel bağlamalar. <xref:System.ServiceModel.BasicHttpBinding> Kullanılmıyor WS adresleme varsayılan olarak yapar, ancak bunu simetrik anahtar tabanlı güvenlik, bu saldırıya karşı savunmasız izin veren şekilde kullanmıyor.  
  
 Özel bağlamalar azaltma güvenlik bağlamı kurmak değil veya WS adresleme üstbilgileri gerektirecek şekilde kullanmaktır.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web grubu: Saldırgan yürütmelerini isteği birden çok düğüme  
 Bir istemci bir Web grubuna uygulanan bir hizmet kullanır. Bir saldırgan gruptaki başka bir düğüme gruptaki bir düğüm için gönderilen bir istek başlayarak yeniden oynatılır. Bir hizmeti yeniden başlatılırsa, ayrıca, tekrar yürütme önbelleğine, isteği yeniden göndermek bir saldırgan izin vererek temizlenir. (Önbellek kullanılan, daha önce görülen ileti imzası değerler içeriyor ve bu imzaların yalnızca bir kez kullanılabilmesi için yürütmelerini önler. Yeniden yürütme önbellekleri bir Web grubu arasında paylaşılmaz.)  
  
 Azaltıcı Etkenler şunlardır:  
  
-   İleti modu güvenlik durum bilgisi olan güvenlik bağlamı belirteçleri (ile veya etkin güvenli konuşma olmadan) kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Hizmetini aktarım düzeyinde güvenlik kullanacak şekilde yapılandırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
