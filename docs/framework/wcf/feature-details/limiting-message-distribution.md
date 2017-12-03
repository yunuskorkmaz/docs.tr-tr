---
title: "İleti Dağıtımını Sınırlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 191baa2df4a6a5a4fe8139e8b7ad36bd1c60b40d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="limiting-message-distribution"></a>İleti Dağıtımını Sınırlandırma
Eş kanal yayın kafes tasarım gereğidir. Bu ağ, diğer tüm üyelerine kafes herhangi bir üyesi tarafından gönderilen her ileti dağıtma kendi temel flooding modelini içerir. Bu, her ileti bir üyesi tarafından oluşturulan tüm diğer üyeler için (örneğin, sohbet odası) ilgili ve faydalı olduğu durumlarda idealdir. Bununla birlikte, birçok uygulamanın ileti dağıtımını sınırlandırma bir nadiren ihtiyaç vardır. Yeni bir üye kafes birleştirir ve ağ gönderilen son ileti almak istiyorsa, örneğin, bu istek kafes her üyesine taşan olması gerekmez. Yerel olarak oluşturulmuş iletileri filtrelenebilen veya istek Komşuları yakınında sınırlı olabilir. İletileri kafes tek tek bir düğümde yeniden gönderilebilir. Bu konu, iletileri kafes nasıl iletilen denetlemek için atlama sayısı, bir ileti yayma filtresi, yerel bir filtre veya doğrudan bir bağlantı kullanarak açıklar ve bir yaklaşım seçimi için genel yönergeler sağlar.  
  
## <a name="hop-counts"></a>Atlama sayısı  
 Kavramı `PeerHopCount` IP protokolü kullanılan bir TTL (Time-To-Live) benzer. Değeri `PeerHopCount` bir ileti örneğine bağlanır ve bir ileti iletilen bırakılan önce kaç kez belirtir. Bir ileti eş kanalı istemci tarafından alınan her zaman istemci iletisi olup olmadığını inceler `PeerHopCount` belirtilir. Belirtilmişse, ardından istemci azaltır atlama sayısı değeri tek komşu düğümler iletiye iletilmeden önce. Bir istemci sıfır atlama sayısı değeri içeren bir ileti aldığında, istemci iletisini işler, ancak iletiyi Komşuları için iletme değil.  
  
 Atlama sayısı eklenebilir bir iletiye ekleyerek `PeerHopCount` geçerli özellik veya alan uygulamasında ileti sınıfı için bir öznitelik olarak. Bu iletiyi kafes göndermeden önce belirli bir değere ayarlayabilirsiniz. Bu şekilde, atlama sayısı olası gereksiz ileti çoğaltma önleme gerektiğinde kafes iletileri dağıtımını sınırlamak için kullanabilirsiniz. Bu, yedek veri ya da hemen Komşuları veya Komşuları birkaç durak içinde bir ileti göndermek için yüksek bir miktar kafes içerdiği durumlarda yararlıdır.  
  
-   Kod parçacıkları ve ilgili bilgi için bkz: [eş kanalı blog](http://go.microsoft.com/fwlink/?LinkID=114531) (http://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>İleti yayma filtresi  
 `MessagePropagationFilter`özellikle ileti veya diğer belirli senaryolar içeriğini karar verirken yayma ileti, taşmasını özelleştirilmiş denetim için kullanılabilir. Filtre düğümünden geçirir her ileti yayma kararlarını verir. Bu, başka bir yerde düğümünüz uygulamanız tarafından oluşturulan iletiler yanı sıra aldı kafes kaynaklanan iletileri için geçerlidir. Filtre ileti ve onun oluşturulma erişim sahiptir, bu nedenle iletme veya ileti siliniyor hakkında kararlar kullanılabilir tam bilgilerine dayalı.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter>tek bir işlevi ile temel bir Özet sınıf <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Yöntem çağrısının ilk bağımsız değişkeni ileti tam bir kopyasını geçirir. İletiye yapılan değişiklikler gerçek ileti etkilemez. Yöntem çağrısının son bağımsız değişkeni iletinin kaynağını tanımlar (`PeerMessageOrigination.Local` veya `PeerMessageOrigination.Remote`). Bu yöntem, somut uygulamalarını içinden bir sabit döndürmelidir <xref:System.ServiceModel.PeerMessagePropagation> numaralandırma ileti yerel uygulama iletilecek olduğunu belirten (`Local`), uzak istemcilere iletilen (`Remote`), her iki (`LocalAndRemote`), veya hiçbiri (`None`). Bu filtre, karşılık gelen erişerek uygulanabilir `PeerNode` nesne ve türetilen yayma örneği belirterek filtre sınıfında `PeerNode.MessagePropagationFilter` özelliği. Eş kanal açmadan önce yayma filtre bağlı olduğundan emin olun.  
  
-   Kod parçacıkları ve ilgili bilgi için bkz: [eş kanalı blog](http://go.microsoft.com/fwlink/?LinkID=114532) (http://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Tek bir ağ düğümünde bağlantı kuruluyor  
 Tek bir ağ düğümünde, yerel bir filtre ayarlayarak veya doğrudan bir bağlantı kurma ulaşılabilir.  
  
 Her bir kafes düğümlerin tek tek bir Kimliğiniz varsa, bir hedef kimliği iletinizi uygulamasında belirtilebilir. Yerel bir filtre Kimliğini, belirtilen hedef kimliği eşleşirse, yalnızca geçerli düğüme ileti görüntülenir, ileti sözleşmesi işlevi yazarak ayarlanabilir. Yeni bir bağlantı kurma yükünü ücrete tabi yok şekilde kafes ileti taşımaları. Ancak, ileti kafes defalarca göndermesinden itibaren geçen verimliliği kaybı yoktur. Bu, çok büyük veya çok sık ileti sürece iyi ileti tek bir kafes üyelerine göndermek için çalışır.  
  
 Uzun süre dayanan, yüksek bant genişliği bağlantılarında doğrudan bağlantılar tercih edilir. Bağlantı bilgilerini ağ göndermek ve iletileri Gönder/Al seçme doğrudan bir bağlantı ayarlayın.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>İleti dağıtımını sınırlandırma için bir yaklaşım seçme  
 İleti dağıtımını sınırlamak gereken bir senaryo bulduğunuzda, aşağıdaki soruları kendinize sorun:  
  
-   **Kimin** iletisi gerekiyor? Yalnızca bir Komşu düğüm? Bir düğüm başka bir yere kafes? Yarı kafes?  
  
-   **Ne sıklıkta** Bu mesajı gönderilir?  
  
-   Ne tür, **bant genişliği** bu iletiyi kullanacaksınız?  
  
 Bu sorulara verdiğiniz yanıtlar, atlama sayısı, bir ileti yayma filtresi, yerel bir filtre veya doğrudan bir bağlantı kullanılıp kullanılmayacağını belirlemenize yardımcı olabilir. Aşağıdaki genel yönergeleri dikkate alın:  
  
-   **Kimin**  
  
    -   *Tek düğüm*: Yerel filtre veya doğrudan bağlantı.  
  
    -   *Belirli bir yakın çevre içinde Komşuları*: PeerHopCount.  
  
    -   *Mesh karmaşık alt*: MessagePropagationFilter.  
  
-   **Ne sıklıkta**  
  
    -   *Çok sık*: doğrudan bağlantı, PeerHopCount, MessagePropagationFilter.  
  
    -   *Zaman zaman*: Yerel filtre.  
  
-   **Bant genişliği kullanımı**  
  
    -   *Yüksek*: doğrudan bağlantı, MessagePropagationFilter veya yerel filtre kullanmak için daha az önerilir.  
  
    -   *Düşük*: büyük olasılıkla gereken herhangi biri doğrudan bağlantı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
