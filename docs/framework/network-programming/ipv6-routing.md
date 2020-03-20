---
title: IPv6 Yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047783"
---
# <a name="ipv6-routing"></a>IPv6 Yönlendirme
Esnek yönlendirme mekanizması IPv6'nın bir avantajıdır. IPv4 ağ iD'lerinin ayrılma ve ayrılma biçimi nedeniyle, büyük yönlendirme tablolarının Internet omurgasında bulunan yönlendiriciler tarafından korunması gerekir. Bu yönlendiriciler, Internet'teki herhangi bir düğüme yönlendirilmiş olabilecek paketleri iletmek için tüm yolları bilmesi gerekir. Adresleri toplama yeteneği yle IPv6 esnek adresleme sağlar ve yönlendirme tablolarının boyutunu büyük ölçüde azaltır. Bu yeni adresleme mimarisinde, ara yönlendiriciler iletileri uygun şekilde iletmek için yalnızca ağlarının yerel bölümünü izlemelidir.  
  
## <a name="neighbor-discovery"></a>Komşu Bulma  
 Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:  
  
- Yönlendirici keşfi. Bu, ana bilgisayarların yerel yönlendiricileri tanımlamasına olanak tanır.  
  
- Adres çözünürlüğü. Bu, düğümlerin karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü [ARP] yerine bir bağlantı katmanı adresi çözmesine olanak tanır.  
  
- Adres otomatik yapılandırma. Bu, ana bilgisayarların site yerel ve genel adreslerini otomatik olarak yapılandırmasına olanak tanır.  
  
 Komşu Bulma, IPv6 (ICMPv6) iletileri için:  
  
- Yönlendirici reklam. Bir yönlendirici tarafından sözde periyodik olarak veya yönlendirici talebine yanıt olarak gönderilir. IPv6 yönlendiricileri kullanılabilirliklerini, adres öneklerini ve diğer parametreleri bildirmek için yönlendirici reklamları kullanır.  
  
- Yönlendirici talebi. Bağlantıdaki yönlendiricilerin hemen bir yönlendirici reklamı göndermesini istemek için bir ana bilgisayar tarafından gönderilir.  
  
- Komşu talebi. Adres çözümlemesi, yinelenen adres algılamaveya komşunun hala ulaşılabilir olduğunu doğrulamak için düğümler tarafından gönderilir.  
  
- Komşu reklamı. Bir komşu talebine yanıt vermek veya bağlantı katmanı adresindeki bir değişikliği komşuları bilgilendirmek için düğümler tarafından gönderilir.  
  
- Yönlendirme. Yönlendiriciler tarafından, gönderen düğüm için belirli bir hedefe daha iyi bir sonraki atlama adresini belirtmek için gönderilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
