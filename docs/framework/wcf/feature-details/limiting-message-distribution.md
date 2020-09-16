---
title: İleti Dağıtımını Sınırlandırma
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: e736aba60d7d2b39d1b8eb958a8c72e6e8d55e13
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555022"
---
# <a name="limiting-message-distribution"></a>İleti Dağıtımını Sınırlandırma

Eş kanal, yayın ağı tasarlayabilme. Temel taşması modeli, bir kafesin herhangi bir üyesi tarafından gönderilen her iletiyi o kafesin diğer üyelerine dağıtmayı içerir. Bu, bir üye tarafından oluşturulan her iletinin ilgili olduğu ve diğer tüm Üyeler için (örneğin, bir sohbet odası) yararlı olduğu durumlarda idealdir. Ancak, birçok uygulamanın ileti dağıtımını kısıtlamak için zaman zaman ihtiyacı vardır. Örneğin, yeni bir üye bir kafesi birleştirir ve ağ üzerinden gönderilen son iletiyi almak istiyorsa, bu isteğin her ağ üyesine taşmasının gerekli değildir. İstek yakın komşular ile sınırlandırılabilir veya yerel olarak oluşturulan iletiler filtrelenebilir. İletiler Ayrıca, kafesde tek bir düğüme gönderilebilir. Bu konuda atlama sayısı, Ileti yayma filtresi, yerel bir filtre veya iletilerin ağ genelinde nasıl iletildiğini denetlemek için doğrudan bağlantı kullanımı ele alınmaktadır ve bir yaklaşım seçmek için genel yönergeler sağlanmaktadır.

## <a name="hop-counts"></a>Atlama sayısı

Kavramı, `PeerHopCount` IP protokolünde kullanılan TTL (yaşam süresi) ile benzerdir. Değeri `PeerHopCount` bir ileti örneğine bağlıdır ve bir iletinin bırakılmadan önce kaç kez iletilmesi gerektiğini belirtir. Bir eş kanal istemcisi tarafından bir ileti alındığında istemci, belirtilen olup olmadığını görmek için iletiyi inceler `PeerHopCount` . Belirtilmişse, istemci, iletiyi komşu düğümlere iletmeden önce atlama sayısı değerini bir azaltır. İstemci atlama sayısı değeri sıfır olan bir ileti aldığında, istemci iletiyi işler, ancak iletiyi komşuları 'e iletmez.

`PeerHopCount`İleti sınıfı uygulamasındaki uygulanabilir özelliğe veya alana bir öznitelik olarak eklenerek atlama sayısı bir iletiye eklenebilir. İletiyi ağ üzerinden göndermeden önce belirli bir değere ayarlayabilirsiniz. Bu şekilde, gerekli olduğunda, ağ genelinde iletilerin dağıtımını sınırlandırmak için atlama sayısı ' nı kullanabilir, böylece gereksiz ileti yinelemeyi önleyebilirsiniz. Bu, kafesin yüksek miktarda yedekli veri içerdiği ya da anında komşular veya birkaç atlamanın içindeki komşular için bir ileti göndermede yararlı olur.

- Kod parçacıkları ve ilgili bilgiler için bkz. [PeerHopCount özniteliği:](/archive/blogs/peerchan/the-peerhopcount-attribute-controlling-message-distribution) eş kanal blogundan ileti dağıtımı gönderisini denetleme.

## <a name="message-propagation-filter"></a>İleti yayma filtresi

`MessagePropagationFilter` Özellikle iletinin içeriği veya diğer belirli senaryolar yayılmayı tespit edildiğinde ileti taşmasını özelleştirilmiş denetim için kullanılabilir. Filtre, düğüm üzerinden geçen her ileti için yayma kararları verir. Bu, bir yerde, düğümünüz ve uygulamanız tarafından oluşturulan iletilerin başka bir yerinde oluşan iletiler için geçerlidir. Filtrenin hem iletiye hem de kaynağına erişimi vardır; bu nedenle iletiyi iletme veya bırakma hakkında kararlar, kullanılabilir olan tüm bilgileri temel alabilir.

<xref:System.ServiceModel.PeerMessagePropagationFilter> , tek bir işlevi olan temel soyut bir sınıftır <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A> . Yöntem çağrısının ilk bağımsız değişkeni iletinin tam bir kopyasında geçirilir. İletide yapılan tüm değişiklikler gerçek iletiyi etkilemez. Yöntem çağrısının son bağımsız değişkeni iletinin kaynağını tanımlar ( `PeerMessageOrigination.Local` veya `PeerMessageOrigination.Remote` ). Bu yöntemin somut uygulamaları, iletinin yerel uygulamaya () iletileceği, uzak istemcilere () () () (), <xref:System.ServiceModel.PeerMessagePropagation> `Local` ya da `Remote` `LocalAndRemote` ne () iletildiğini belirten `None` sabit listesinden bir sabit döndürmelidir. Bu filtre, ilgili `PeerNode` nesneye erişerek ve özelliğindeki türetilmiş yayma filtresi sınıfının bir örneğini belirterek uygulanabilir `PeerNode.MessagePropagationFilter` . Eş kanalını açmadan önce yayma filtresinin eklendiğinden emin olun.

- Kod parçacıkları ve ilgili bilgiler için, eş kanal bloguna [eş kanal ve MessagePropagationFilter](/archive/blogs/peerchan/peer-channel-and-messagepropagationfilter) gönderisine bakın.

## <a name="contacting-an-individual-node-in-the-mesh"></a>Kafesteki tek bir düğümle iletişim kurma

Bir kafesteki tek bir düğüme yerel bir filtre ayarlanarak veya doğrudan bağlantı ayarlanarak iletişim kurulabilirler.

Bir kafesdeki düğümlerin tek bir KIMLIĞI varsa, iletinizin uygulamasında bir hedef KIMLIĞI belirtilebilir. İleti sözleşmeniz, KIMLIĞI belirttiğiniz hedef KIMLIĞIYLE eşleşiyorsa iletiyi yalnızca geçerli düğüme görüntüleyecek olan bir işlev yazılarak ayarlanabilir. Ağ, iletiyi taşır, bu nedenle yeni bir bağlantı kurma yükünün tahakkuk olması gerekmez. Ancak, ağ genelinde iletinin birçok kez gönderilmesi için bir verimlilik kaybı vardır. Bu, iletiler çok büyük veya çok sık olmadığı sürece bir kafesin ayrı üyelerine ileti göndermek için iyi bir sonuç verir.

Uzun süreli, yüksek bant genişliğine sahip bağlantılarda doğrudan bağlantılar tercih edilir. Ağ üzerinden bağlantı bilgilerini gönderebilir ve ardından ileti gönderme/alma seçeneğini belirleyerek doğrudan bir bağlantı kurabilirsiniz.

## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Ileti dağıtımını kısıtlamak için bir yaklaşım seçme

İleti dağıtımını sınırlandırmanız gereken bir senaryo keşfettiğiniz zaman, aşağıdaki soruları kendinize sorun:

- İletiyi alması gereken **kişiler** ? Yalnızca bir komşu düğüm mi? Bir düğüm, kafeste başka bir yerde mi? Kafesin yarısı mi?

- Bu ileti **ne sıklıkla** gönderilir?

- Bu ileti ne tür bir **bant genişliğine** kullanacaktır?

Bu soruların yanıtları, atlama sayısı, Ileti yayma filtresi, yerel bir filtre veya doğrudan bağlantı kullanıp kullanmayacağınızı belirlemenize yardımcı olabilir. Aşağıdaki genel yönergeleri göz önünde bulundurun:

- **Sağlayan**

  - *Bağımsız düğüm*: Yerel filtre veya doğrudan bağlantı.

  - *Belirli bir yakın çevre Içinde komşuları*: PeerHopCount.

  - *Kafesin karmaşık alt kümesi*: MessagePropagationFilter.

- **Ne sıklıkta**

  - *Çok sık*: doğrudan bağlantı, PeerHopCount, MessagePropagationFilter.

  - *Zaman zaman*: Yerel filtre.

- **Bant genişliği kullanımı**

  - *Yüksek*: doğrudan bağlantı, MessagePropagationFilter veya yerel filtre kullanmak daha az önerilir.

  - *Düşük*: herhangi bir, doğrudan bağlantı gerekli değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)
