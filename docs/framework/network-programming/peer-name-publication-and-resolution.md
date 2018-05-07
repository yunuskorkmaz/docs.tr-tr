---
title: Eş adı yayını ve çözümleme
ms.date: 03/30/2017
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4e64f1293da18823166883a869ac6377908c9e72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="peer-name-publication-and-resolution"></a>Eş adı yayını ve çözümleme
## <a name="publishing-a-peer-name"></a>Eş adı yayımlama  
 Yeni bir PNRP kimliği yayımlamak için bir eş aşağıdakileri gerçekleştirir:  
  
-   Önbellek Komşuları (PNRP kimlikleri en düşük düzeyde önbellek kaydettiniz eş) PNRP yayın iletileri gönderir kendi önbellekleri oluşturmak için.  
  
-   Rastgele düğümleri, komşularına olmayan bulutta seçer ve bunları kendi P2P kimliği için PNRP ad çözümleme isteklerini gönderir Sonuçta elde edilen uç nokta belirleme işlemi bulutta rastgele düğümleri önbellekleri yayımlama eş PNRP kimliği çekirdeğini oluşturur.  
  
-  
  
 Yalnızca diğer P2P kimlikler çözümleniyor, PNRP sürüm 2 düğümleri PNRP kimlikleri yayımlamayın. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PeerNet\PNRP\IPV6 Global\SearchOnly = 1 kayıt defteri değeri (REG_DWORD türü) eşleri yalnızca PNRP hiçbir zaman ad yayını için ad çözümlemesi için kullandığınız belirtir. Bu kayıt defteri değerini de Grup İlkesi aracılığıyla yapılandırılabilir.  
  
## <a name="resolving-a-peer-name"></a>Eş adı çözümleme  
 Bir PNRP diğer eş konumlandırma ağ veya Bulut iki aşamaları oluşan bir işlemdir:  
  
1.  Uç nokta belirleme  
  
2.  PNRP Kimliğine çözümleme  
  
 Uç nokta belirleme aşamasında, başka bir bilgisayardaki bir hizmet PNRP Kimliğini çözümlemeyi deniyor bir eş o uzak eş IPv6 adresini belirler.  Uzak eş yayımlanan ya da bilgisayar veya hizmetin PNRP kimliği ile ilişkili adrestir.  
  
 Uzak uç nokta PNRP bulutunu kayıtlı olduğunu doğruladıktan sonra istekte bulunan eşi PNRP kimliği çözümleme aşamasında bir istek bu eş uç noktasına istenen hizmeti için PNRP Kimliğini gönderir. Uç hizmeti, bir açıklama PNRP Kimliğini onaylayan bir yanıt gönderir ve ek bilgi isteyen eş, 4 KB'ye kadar gelecekteki iletişim için kullanabilirsiniz. Örneğin, istenen son nokta bir oyun sunucusu ise, ek Eş adı kayıt veri oyun, play düzeyini ve oyuncu geçerli sayısını hakkında bilgiler içerebilir.  
  
 Uç nokta belirleme aşamasında, PNRP çözümlemesinde düğümü hedef PNRP kimliği sırayla daha yakın olan düğümleri kurmakla sorumlu kimliği yayımlanan düğümü bulmak için yinelemeli süreç PNRP kullanır  
  
 İçinde PNRP ad çözümlemesi için hedef PNRP kimliği ile eşleşen bir girdi için kendi önbelleğindeki girişleri eş inceler Bulunursa, eş eşler arası bir PNRP istek iletisi gönderir ve yanıt bekler. Eş PNRP istek iletisi PNRP kimliği için bir giriş bulunmazsa, hedef PNRP kimliği en yakından eşleşen bir PNRP Kimliğine sahip girişine karşılık gelen eş gönderir. PNRP İstek iletisini alır düğüm, kendi önbellek inceler ve şunları yapar:  
  
-   PNRP kimlik bulunmazsa, istenen endpoint eş doğrudan isteyen eşler arası yanıtlar.  
  
-   PNRP kimliği bulunamadı ve PNRP kimliği önbelleğinde hedef PNRP kimliği yakın ise, istenen eş hedef PNRP kimliği daha yakından eşleşen bir PNRP kimliği ile girişini temsil eden eş IPv6 adresini içeren isteyen eş yanıt gönderir. Yanıtta IP adresini kullanarak isteyen düğümün yanıt veya önbelleğinde incelemek için IPv6 adresi için başka bir PNRP istek iletisi gönderir.  
  
-   PNRP kimliği bulunamadı ve PNRP kimliği yok hedef PNRP kimliği daha yakın olan kendi önbelleğinde yoksa, istenen eş isteyen eş bu koşulu belirten bir yanıt gönderir. İstekte bulunan eş sonraki en yakın PNRP kimliği sonra seçer.  
  
-  
  
 İstekte bulunan eş sonunda PNRP kimliği kayıtlı düğüm bulunuyor art arda yineleme, bu işlemle devam eder  
  
 İçinde <xref:System.Net.PeerToPeer> ad alanı, arasında çok-çok ilişkisi olduğundan <xref:System.Net.PeerToPeer.PeerName> uç noktaları ve PNRP Bulut veya görüntüleneceği iletişim kurarlar kafesleri içeren kaydeder. Çoğaltılmış veya eski girişleri veya birden çok düğümün aynı eş ada sahip olduğunuzda PNRP düğümleri geçerli bilgileri kullanarak elde edebilirsiniz <xref:System.Net.PeerToPeer.PeerNameResolver> sınıfı. <xref:System.Net.PeerToPeer.PeerNameResolver> Yöntemleri bir eş çok eş ad kayıtlarını perspektife ve aynı bir eşler arası birçok Bulutlar basitleştirmek için tek eş adını kullanın. Bu tablodan ilişkisel birleştirme kullanılarak gerçekleştirilen bir sorguya benzer. Çözümleyici nesnesi başarıyla tamamlandıktan sonra döndürür bir <xref:System.Net.PeerToPeer.PeerNameRecordCollection> belirtilen Eş adı.  Örneğin, bir eş adı koleksiyondaki tüm eş ad kayıtları oluşacak bulut tarafından sıralanan. Bu destek verisini PNRP tabanlı bir uygulama tarafından istenebilir Eş adı örnekleridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer>
