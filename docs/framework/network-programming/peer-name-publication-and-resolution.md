---
description: 'Daha fazla bilgi edinin: eş adı yayınlama ve çözümleme'
title: Eş Adı Yayını ve Çözümleme
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: cd1d3358c212b1618548422715329eea57452ac3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747432"
---
# <a name="peer-name-publication-and-resolution"></a>Eş Adı Yayını ve Çözümleme

## <a name="publishing-a-peer-name"></a>Eş adı yayımlama  

 Yeni bir PNRP KIMLIĞI yayımlamak için, bir eş şunları gerçekleştirir:  
  
- , Önbelleklerini temel almak için, bir ön bellek komşuları (en düşük önbellek düzeyinde kayıtlı PNRP kimlikleri olan Peers) olan bir PNRP yayın iletisi gönderir.  
  
- Bulutta, komşuları olmayan rastgele düğümleri seçer ve kendisine kendi P2P KIMLIĞI için PNRP ad çözümleme istekleri gönderir. Elde edilen uç nokta belirleme işlemi, bulutta bulunan rastgele düğümlerin önbelleklerini yayımlama eşinin PNRP KIMLIĞIYLE depolar.  
  
PNRP sürüm 2 düğümleri yalnızca diğer P2P kimliklerini çözümlerse PNRP kimliklerini yayımlamaz. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 kayıt defteri değeri (REG_DWORD türü), eşler ad yayımlama için hiçbir koşulda yalnızca ad çözümlemesi için PNRP kullanacağınızı belirtir. Bu kayıt defteri değeri, grup ilkesi aracılığıyla da yapılandırılabilir.  
  
## <a name="resolving-a-peer-name"></a>Eş adı çözme

 Bir PNRP ağı veya bulutu 'ndaki diğer eşleri bulmak iki aşamadan oluşan bir işlemdir:  
  
1. Uç nokta belirleme  
  
2. PNRP KIMLIK çözümlemesi  
  
 Uç nokta belirleme aşamasında, başka bir bilgisayardaki bir hizmetin PNRP KIMLIĞINI çözümlemeye çalışan bir eş, o uzak eşin IPv6 adresini belirler.  Uzak eş, bilgisayar veya hizmetin PNRP KIMLIĞI olan veya ile ilişkili olan veya ilişkilendirildiği bir bilgisayardır.  
  
 Uzak bitiş noktasının PNRP bulutuna kayıtlı olduğunu onayladıktan sonra, bu eş uç noktasına, istenen hizmetin pnrp kimliği için bir istek gönderir. Uç noktası, hizmet PNRP KIMLIĞI, bir açıklama ve istek eşi tarafından daha sonra iletişim için kullanılabilecek 4 kilobayt daha fazla bilgi onaylayan bir yanıt gönderir. Örneğin, istenen uç nokta bir oyun sunucusu ise, ek eş adı kayıt verileri oyun, yürütme düzeyi ve geçerli oyuncu sayısı hakkında bilgiler içerebilir.  
  
 Endpoint belirleme aşamasında, PNRP, çözümleme gerçekleştiren düğümün hedef PNRP KIMLIĞINE çok daha yakın olan düğümlere iletişim sağlamaktan sorumlu olduğu PNRP KIMLIĞINI yayımlayan düğümü bulmak için yinelemeli bir işlem kullanır.  
  
 PNRP 'de ad çözümlemesi gerçekleştirmek için, eş, hedef PNRP KIMLIĞIYLE eşleşen bir giriş için kendi önbelleğindeki girişleri inceler. Bulunursa, eş, eşe bir PNRP Istek iletisi gönderir ve bir yanıt bekler. PNRP KIMLIĞI için bir giriş bulunamazsa, eş, hedef PNRP KIMLIĞIYLE en yakından eşleşen bir PNRP KIMLIĞI olan girdiye karşılık gelen bir PNRP Istek iletisi gönderir. PNRP Istek iletisini alan düğüm kendi önbelleğini inceler ve şunları yapar:  
  
- PNRP KIMLIĞI bulunursa, istenen uç nokta eşi doğrudan istekte bulunan eşe yanıt verir.  
  
- PNRP KIMLIĞI bulunmazsa ve önbellekteki bir PNRP KIMLIĞI hedef PNRP KIMLIĞINE yakınsa, istenen eş, hedef PNRP KIMLIĞIYLE daha yakından eşleşen bir PNRP KIMLIĞINE sahip girişi temsil eden, istek yapan eşe bir yanıt gönderir. Yanıttaki IP adresini kullanarak, istenen düğüm, önbelleğini yanıtlamak veya incelemek üzere IPv6 adresine başka bir PNRP Istek iletisi gönderir.  
  
- PNRP KIMLIĞI bulunmazsa ve önbelleğinde hedef PNRP KIMLIĞINE daha yakın bir PNRP KIMLIĞI yoksa, istenen eş istek isteğini bu koşulu gösteren bir yanıt gönderir. İstekte bulunan eş daha sonra bir sonraki en yakın PNRP KIMLIĞINI seçer.  
  
İstekte bulunan eş, bu işlemi izleyen yinelemelerle devam ettirir ve sonuçta PNRP KIMLIĞINI kaydetmiş olan düğümü bulur.  
  
 <xref:System.Net.PeerToPeer>Ad alanı içinde, <xref:System.Net.PeerToPeer.PeerName> uç noktaları ve bunların iletişim kurdukları iş kafesleri içeren kayıtlar arasında çoktan çoğa bir ilişki vardır. Yinelenen veya eski girişler veya aynı eş adına sahip birden çok düğüm olduğunda, PNRP düğümleri sınıfı kullanarak geçerli bilgileri elde edebilir <xref:System.Net.PeerToPeer.PeerNameResolver> . <xref:System.Net.PeerToPeer.PeerNameResolver>Yöntemler tek bir eş adı kullanır ve birden çok eş ad kaydına yönelik perspektifi ve birden çok bulutta aynı eşi kolaylaştırır. Bu, ilişkisel tablo JOIN kullanılarak gerçekleştirilen bir sorgu ile benzerdir. Başarıyla tamamlandıktan sonra, çözümleyici nesnesi <xref:System.Net.PeerToPeer.PeerNameRecordCollection> belirtilen eş adı için bir döndürür.  Örneğin, koleksiyondaki tüm eş adı kayıtlarında bir eş adı meydana gelir ve buluta göre sıralanır. Bunlar, destekleyen verileri bir PNRP tabanlı uygulama tarafından istenmiş olan eş adı örnekleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
