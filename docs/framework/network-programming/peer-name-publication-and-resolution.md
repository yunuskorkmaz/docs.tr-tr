---
title: Eş Adı Yayını ve Çözümleme
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 4a0787972a61f5700d1e8728be96db8ef9ee749e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623194"
---
# <a name="peer-name-publication-and-resolution"></a>Eş Adı Yayını ve Çözümleme

## <a name="publishing-a-peer-name"></a>Eş adı yayımlama  

 Yeni bir PNRP kimliği yayımlamak için eş aşağıdakileri gerçekleştirir:  
  
- Önbelleklerini tohumlamak için önbellek komşularına (önbelleğin en alt düzeyinde PNRP KIMLIKLERINI kaydetmiş olan eşler) PNRP yayın iletileri gönderir.  
  
- Bulutta komşuları olmayan rasgele düğümleri seçer ve onlara kendi P2P kimliği için PNRP ad çözümleme istekleri gönderir. Elde edilen uç nokta belirleme işlemi, yayımcı eşin PNRP Kimliği ile buluttaki rasgele düğümöneklerini tohumlar.  
  
PNRP sürüm 2 düğümleri, yalnızca diğer P2P iD'lerini çözüyorsa PNRP iDileri yayımlamaz. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6-Global\SearchOnly=1 kayıt defteri değeri (REG_DWORD türü) eşler, ad yayımı için asla ad çözümlemesi için yalnızca PNRP'yi kullandıklarını belirtir. Bu kayıt defteri değeri Grup İlkesi aracılığıyla da yapılandırılabilir.  
  
## <a name="resolving-a-peer-name"></a>Eş adını çözme

 Bir PNRP ağında veya bulutta diğer eşleri bulmak iki aşamadan oluşan bir işlemdir:  
  
1. Uç Nokta Belirleme  
  
2. PNRP Kimlik Çözünürlüğü  
  
 Bitiş noktası belirleme aşamasında, başka bir bilgisayardaki bir hizmetin PNRP kimliğini çözmeye çalışan bir eş, o uzak eşin IPv6 adresini belirler.  Uzak eş, bilgisayarın veya hizmetin PNRP Kimliğini yayımlayan veya bu yla ilişkili olandır.  
  
 Uzak bitiş noktasının PNRP bulutuna kaydedildiğini doğruladıktan sonra, PNRP KIMLIK çözümleme aşamasındaki isteyen eş, istenen hizmetin PNRP Kimliği için bu eş bitiş noktasına bir istek gönderir. Bitiş noktası, hizmetin PNRP Kimliğini, bir yorumu ve isteyen eşin gelecekteki iletişim için kullanabileceği 4 kilobayta kadar ek bilgiyi doğrulayan bir yanıt gönderir. Örneğin, istenen bitiş noktası bir oyun sunucusuysa, ek eş adı kaydı verileri oyun, oyun düzeyi ve geçerli oyuncu sayısı hakkında bilgi içerebilir.  
  
 Uç nokta belirleme aşamasında, PNRP, çözümü gerçekleştiren düğümün hedef PNRP KIMLIĞIne art arda yakın olan düğümlerle temas kurmakndan sorumlu olduğu PNRP Kimliğini yayımlayan düğümü bulmak için yinelemeli bir işlem kullanır.  
  
 PNRP'de ad çözümlemesi gerçekleştirmek için eş, hedef PNRP Kimliğiyle eşleşen bir giriş için kendi önbelleğindeki girişleri inceler. Bulunursa, eş eşe bir PNRP İstek iletisi gönderir ve yanıt bekler. PNRP Kimliği için bir giriş bulunamazsa, eş eş, hedef PNRP Kimliğiile en yakın eşleşen bir PNRP kimliğine sahip girişe karşılık gelen bir PNRP İstek iletisi gönderir. PNRP İstek iletisini alan düğüm kendi önbelleğini inceler ve aşağıdakileri yapar:  
  
- PNRP Kimliği bulunursa, istenen uç nokta eş doğrudan isteyen eşe yanıt verir.  
  
- PNRP Kimliği bulunamazsa ve önbellekteki Bir PNRP Kimliği hedef PNRP Kimliği'ne daha yakınsa, istenen eş, hedefi PNRP Kimliğiile girişi temsil eden eşin IPv6 adresini içeren isteyen eşe bir yanıt gönderir. Yanıttaki IP adresini kullanarak, isteyen düğüm, önbelleğini yanıtlamak veya incelemek için IPv6 adresine başka bir PNRP İstek iletisi gönderir.  
  
- PNRP Kimliği bulunamazsa ve önbelleğinde hedef PNRP Kimliği'ne daha yakın bir PNRP kimliği yoksa, istenen eş isteyen eşe bu durumu gösteren bir yanıt gönderir. İstenen eş, sonraki en yakın PNRP kimliğini seçer.  
  
İstenen eş, sonunda PNRP Kimliğini kaydeden düğümü bularak bu işleme ardışık yinelemelerle devam eder.  
  
 <xref:System.Net.PeerToPeer> Ad alanı içinde, uç noktaları ve pnrp <xref:System.Net.PeerToPeer.PeerName> bulutları veya iletişim kurdukları kafesler içeren kayıtlar arasında çok-çok ilişkisi vardır. Yinelenen veya eski girişler veya aynı eş adına sahip birden çok düğüm olduğunda, PNRP <xref:System.Net.PeerToPeer.PeerNameResolver> düğümleri sınıfı kullanarak geçerli bilgileri edinebilir. Yöntemler, <xref:System.Net.PeerToPeer.PeerNameResolver> eşlerden çok eşe eş adı kayıtlarının perspektifini basitleştirmek için tek bir eş adı ve birçok buluta eş vermek için kullanılır. Bu, ilişkisel tablo birleştirme kullanılarak gerçekleştirilen bir sorguya benzer. Başarılı bir şekilde tamamlandıktan sonra, Çözümleyici nesnesi belirtilen eş adı için bir <xref:System.Net.PeerToPeer.PeerNameRecordCollection> döndürür.  Örneğin, koleksiyondaki tüm eş adı kayıtlarında bulut tarafından sıralanan bir eş adı oluşur. Bunlar, destekleyici verileri PNRP tabanlı bir uygulama tarafından istenebilecek eş adı örnekleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
