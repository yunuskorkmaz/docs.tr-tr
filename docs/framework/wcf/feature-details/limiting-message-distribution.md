---
title: İleti Dağıtımını Sınırlandırma
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: bec5a28abeff23929d2c0f1c363f4e08872a63fa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738652"
---
# <a name="limiting-message-distribution"></a>İleti Dağıtımını Sınırlandırma
Eş kanal yayın kafes tasarım gereğidir. Bu ağ, diğer tüm üyelerine kafes herhangi bir üyesi tarafından gönderilen her ileti dağıtma kendi temel flooding modelini içerir. Bu, her ileti bir üyesi tarafından oluşturulan tüm diğer üyeler için (örneğin, bir sohbet odası) ilgili ve faydalı olduğu durumlarda idealdir. Ancak, birçok uygulama için ileti dağıtımını sınırlandırma bir nadiren ihtiyaç vardır. Yeni bir üye kafes birleştirir ve ağ gönderilen son ileti almayı isteyen, örneğin, bu isteği kafes her üyesi için yığılma olması gerekmez. Yerel olarak oluşturulmuş iletileri filtrelenebilen veya istek Komşuları neredeyse sınırlı olabilir. İletileri kafes tek bir düğümde da gönderilebilir. Bu konu, iletileri kafes nasıl iletilen denetlemek için atlama sayısı, ileti yayma filtresini, yerel bir filtre veya doğrudan bir bağlantı kullanarak açıklar ve bir yaklaşım seçme için genel yönergeleri sağlar.  
  
## <a name="hop-counts"></a>Atlama sayısı  
 Kavramını `PeerHopCount` IP protokolü kullanılan bir TTL (Time-To-Live) benzer. Değerini `PeerHopCount` bir ileti örneğine bağlanır ve bir ileti iletilen bırakılan önce kaç kez belirtir. Bir ileti bir eş kanalı istemci tarafından alınan her zaman istemci olmadığını görmek için ileti inceler `PeerHopCount` belirtilir. Belirtilmişse, ardından istemci atlama sayısını azaltır değeri bir komşu düğümler iletiyi iletme önce. Bir istemci, sıfır atlama sayısı değeri içeren bir ileti aldığında, istemci iletiyi işleyen, ancak iletinin Komşulardan iletmez.  
  
 Atlama sayısı eklenebilir bir ileti ekleyerek `PeerHopCount` geçerli bir özellik veya alan uygulamasında ileti sınıfı için bir özniteliği olarak. Bu iletiyi kafesine göndermeden önce belirli bir değere ayarlayabilirsiniz. Bu şekilde, atlama sayısı büyük olasılıkla gereksiz ileti çoğaltma önleme gerektiğinde, ağı genelinde mesajların sınırlamak için kullanabilirsiniz. Bu, burada kafes yedekli veri ya da hemen Komşuları veya Komşuları birkaç durak içinde bir ileti göndermek için yüksek bir miktar içeren durumlarda kullanışlıdır.  
  
-   Kod parçacıkları ve ilgili bilgi için bkz: [eş kanalı blog](https://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>İleti yayma filtresi  
 `MessagePropagationFilter` özellikle ileti ya da diğer belirli senaryolar içeriğini belirlerken yayılma iletisi, taşmasını özelleştirilmiş denetim için kullanılabilir. Filtre düğümü geçirir her ileti için yayma kararları. Bu, uygulamanız tarafından oluşturulan iletileri yanı sıra düğümünüzü aldı ağ içinde başka bir yerde kaynaklanan iletileri için geçerlidir. Filtre ileti hem kendi kaynağına erişimi olduğundan iletme veya iletinin bırakarak hakkında kararlar kullanılabilir tam bilgileri temel alabilir.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter> tek bir işlev ile temel bir soyut sınıf <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Yöntem çağrısının ilk bağımsız değişken ileti tam bir kopyasını geçirir. İletiye yapılan değişiklikler, gerçek ileti etkilemez. İletinin kaynağını yöntem çağrısının son bağımsız değişken tanımlar (`PeerMessageOrigination.Local` veya `PeerMessageOrigination.Remote`). Bu yöntemin somut uygulamaları, içinden bir sabit döndürmelidir <xref:System.ServiceModel.PeerMessagePropagation> numaralandırma yerel uygulamayı iletilecek iletinin olduğunu belirten (`Local`), uzak istemciler için iletilen (`Remote`), her iki (`LocalAndRemote`), ya da hiçbiri (`None`). Bu filtre, karşılık gelen erişerek uygulanabilir `PeerNode` nesne ve türetilmiş yayma örneğini belirterek filtre sınıfında `PeerNode.MessagePropagationFilter` özelliği. Eş kanal açmadan önce yayma filtre bağlı olduğundan emin olun.  
  
-   Kod parçacıkları ve ilgili bilgi için bkz: [eş kanalı blog](https://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Tek bir ağ düğümünde bağlanılıyor  
 Tek bir ağ düğümünde bir yerel filtre ayarlayarak veya doğrudan bir bağlantı kurma ulaşılabilir.  
  
 Her bir ağ düğümleri tek bir kimliği varsa, iletinizi uygulamasında bir hedef kimliği belirtilebilir. Yerel bir filtre Kimliğini hedef kimliği eşleşiyorsa, yalnızca geçerli düğüm için bir ileti görüntüler, ileti anlaşması bir işlev yazarak ayarlanabilir. Yeni bir bağlantı kurma yükü tahakkuk gerekmez. Bu nedenle kafes iletiyi taşır. Ancak, iletiyi birden çok kez kafes gönderildiği verimlilik kaybı yoktur. Bu, çok büyük veya çok sık ileti olduğu sürece iyi kafes tek tek üyeleri gönderme çalışır.  
  
 Uzun süreli, yüksek bant genişlikli bağlantıları için doğrudan bağlantılar tercih edilir. Bağlantı bilgilerini ağ göndermek ve ileti gönderme ve alma seçtiğiniz doğrudan bir bağlantı ayarlayın.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>İleti dağıtımını sınırlandırma için bir yaklaşım seçme  
 İleti dağıtımını sınırlandırmak istediğiniz bir senaryo bulduğunuzda, kendiniz aşağıdaki soruları sormaya:  
  
-   **Kimin** iletisi gerekiyor? Yalnızca bir komşu düğümü? Bir düğümdeki başka bir yerde kafes? Yarı kafes?  
  
-   **Ne sıklıkta** Bu mesajı gönderilir?  
  
-   Ne tür, **bant genişliği** bu iletiyi kullanacaksınız?  
  
 Bu soruların yanıtlarını atlama sayısı, ileti yayma filtresini, yerel bir filtre veya doğrudan bir bağlantı kullanılıp kullanılmayacağını belirlemenize yardımcı olabilir. Aşağıdaki genel yönergeleri dikkate alın:  
  
-   **Kullanan**  
  
    -   *Tek tek düğüm*: yerel bir filtre veya doğrudan bağlantı.  
  
    -   *Belirli bir çevre içinde Komşuları*: PeerHopCount.  
  
    -   *Karmaşık alt ağı*: MessagePropagationFilter.  
  
-   **Ne sıklıkta**  
  
    -   *Çok sık*: doğrudan bağlantı, PeerHopCount, MessagePropagationFilter.  
  
    -   *Bazen*: Yerel filtre.  
  
-   **Bant genişliğini kullanma**  
  
    -   *Yüksek*: doğrudan bağlantı MessagePropagationFilter veya yerel bir filtre kullanmayı daha az önerilir.  
  
    -   *Düşük*: büyük olasılıkla gerekli herhangi biri doğrudan bir bağlantı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
