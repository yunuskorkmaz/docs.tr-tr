---
title: Eş Adı Yayını ve Çözümleme
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
ms.openlocfilehash: 330117e103f7729ecf6f18ff551f65f1ba0f35da
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309101"
---
# <a name="peer-name-publication-and-resolution"></a>Eş Adı Yayını ve Çözümleme

## <a name="publishing-a-peer-name"></a>Bir eş ad yayımlama  

 Yeni bir PNRP kimliği yayımlamak için bir eş aşağıdakileri gerçekleştirir:  
  
-   Önbellek Komşuları (PNRP kimlikleri önbellek düşük düzeyli kaydolduğundan eşleri) PNRP yayın iletilerini gönderir, önbelleklerini sağlamak için.  
  
-   Komşuları olmayan bulutta rastgele düğümleri seçer ve bunları kendi P2P ID'nin PNRP ad çözümleme isteği gönderir Sonuçta elde edilen uç nokta belirleme işlemi bulutta rastgele düğümlerinin önbellekleri yayımlama eş PNRP kimliği sağlar.  
  
Yalnızca diğer P2P kimlikler çözümleniyor, PNRP sürüm 2 düğümleri PNRP kimlikleri yayımlamayın. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6 Global\SearchOnly = 1 (REG_DWORD türü) kayıt defteri değeri eşleri yalnızca PNRP hiçbir zaman adı yayını için ad çözümlemesi için kullandığınız belirtir. Bu kayıt defteri değerini de Grup İlkesi aracılığıyla yapılandırılabilir.  
  
## <a name="resolving-a-peer-name"></a>Eş adı çözümleme

 Bir PNRP diğer eş konumlandırma ağ veya Bulut iki aşamadan oluşan bir işlemdir:  
  
1. Uç nokta belirleme  
  
2. PNRP kimliği çözümleme  
  
 Uç nokta belirleme aşamasında, başka bir bilgisayardaki bir hizmet PNRP kimliği çözümlemeyi deniyor bir eş o uzak eş IPv6 adresini belirler.  Uzak eş yayımlanan veya bilgisayarı veya hizmeti, PNRP Kimliğini ilişkili adrestir.  
  
 Uzak uç nokta PNRP buluta kayıtlı olduğunu onayladıktan sonra istekte bulunan eş PNRP kimliği çözümleme aşamasında bir isteği bu eş uç noktasına PNRP kimliği için istenen hizmeti gönderir. Uç nokta hizmeti, bir açıklama PNRP Kimliğini onaylayan bir yanıt gönderir ve ek bilgi isteyen eş, 4 KB'ye kadar gelecekteki iletişim için kullanabilirsiniz. Örneğin, istenen uç noktası bir oyun sunucusuysa ek Eş adı kayıt verisi oyun, yürütme düzeyini ve geçerli oyuncu sayısı hakkında bilgiler içerebilir.  
  
 Uç nokta belirleme aşamasında, çözümlemesinde düğümü hedef PNRP kimliği sırayla daha yakın olan düğümleri ile iletişim kurulmasından sorumludur PNRP kimliği yayımlanan düğüm bulmak için bir süreçtir PNRP kullanır  
  
 PNRP ad çözümlemesi için ' % s'hedef PNRP kimlik eşleştiren bir giriş için kendi önbelleğindeki girişleri eş inceler Bulunursa, eş eşler arası PNRP istek ileti gönderir ve bir yanıt bekler. Eş PNRP istek ileti PNRP kimliği için bir giriş bulunmazsa, hedef PNRP kimliği en yakından eşleşen bir PNRP Kimliğine sahip girişe karşılık gelen eş bilgisayara gönderir. PNRP İstek iletisini alır düğümü kendi önbellek inceler ve şunları yapar:  
  
-   PNRP kimlik bulunmazsa, istenen uç noktası eş isteyen eşler arası doğrudan yanıt verir.  
  
-   PNRP kimliği bulunamadı ve önbellekte bir PNRP kimliği hedef PNRP kimliği daha yakından ise, istenen eş isteyen eş IPv6 adresine PNRP kimlikli hedef PNRP kimliği daha yakından eşleşen giriş temsil eden eş içeren bir yanıt gönderir. Yanıtta IP adresini kullanarak, istekte bulunan düğüm yanıt veya önbelleğinde incelemek için IPv6 adresine başka bir PNRP istek iletisi gönderir.  
  
-   PNRP kimliği bulunamadı ve PNRP kimliği yok PNRP kimliği hedefine yakın kendi önbelleğinde yoksa, istenen eş isteyen eş bu koşulu belirten bir yanıt gönderir. İstekte bulunan eş sonraki en yakın PNRP kimliği ardından seçer.  
  
Sonunda PNRP kimliği kayıtlı düğümü bulunurken isteyen eş ardışık yinelemelerde, bu işlem devam ediyor  
  
 İçinde <xref:System.Net.PeerToPeer> ad arasında bir çoktan çoğa ilişki <xref:System.Net.PeerToPeer.PeerName> uç noktaları ve PNRP Bulutları veya içinde iletişim kurarlar kafesleri içeren kayıt. Eş aynı ada sahip birden çok düğüm veya yinelenen ya da eski girişleri olduğunda, PNRP düğümleri geçerli bilgileri kullanarak elde edebilirsiniz <xref:System.Net.PeerToPeer.PeerNameResolver> sınıfı. <xref:System.Net.PeerToPeer.PeerNameResolver> Yöntemleri bir eş çok eş ad kayıtlarını perspektife ve pek çok bulutunuz için aynı bir eş basitleştirmek için çoklu eş adını kullanın. Bu, bir ilişkisel tabloya birleşim kullanılarak gerçekleştirilen bir sorguya benzer. İşlemin başarıyla tamamlanmasından sonra çözümleyici nesnesi döndüren bir <xref:System.Net.PeerToPeer.PeerNameRecordCollection> belirtilen Eş adı.  Örneğin, bir eş ad koleksiyondaki tüm eş ad kayıtlarındaki oluşacak bulut tarafından sıralı. Bu destek verisini PNRP tabanlı bir uygulama tarafından istenebilir Eş adı örnekleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
