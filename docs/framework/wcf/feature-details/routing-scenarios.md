---
title: Yönlendirme Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: 455a6e42aea064d48846994b4e729b90667bc8e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590507"
---
# <a name="routing-scenarios"></a>Yönlendirme Senaryoları
Yönlendirme hizmeti yüksek düzeyde özelleştirilebilir olsa da, sıfırdan yeni bir yapılandırma oluştururken etkili yönlendirme mantığı tasarlamak zor olabilir.  Ancak, birçok yönlendirme hizmeti yapılandırmasının izlediği yaygın senaryolar vardır. Bu senaryolar özel yapılandırmanıza doğrudan uygulanmayabilir, ancak yönlendirme hizmetinin bu senaryoları işlemek üzere nasıl yapılandırılabileceğini anlamak, yönlendirme hizmetini anlamak için size yardımcı olur.  
  
## <a name="common-scenarios"></a>Genel Senaryolar  
 Yönlendirme hizmetinin en temel kullanımı, istemci uygulamalarına sunulan uç noktaların sayısını azaltmak için birden çok hedef uç noktasını toplamaktır ve ardından her iletiyi doğru hedefe yönlendirmek için ileti filtrelerini kullanır. İletiler, belirli bir hizmet tarafından işlenmesi gereken bir ileti türü gibi mantıksal veya fiziksel işleme gereksinimlerine bağlı olarak veya belirli bir kaynaktaki iletilerin öncelik işlemesini sağlamak gibi rastgele iş gereksinimlerine bağlı olarak yönlendirilebilir. Aşağıdaki tabloda bazı yaygın senaryolar ve bunların ne zaman karşılaşıldığı listelenmiştir:  
  
|Senaryo|Şu durumlarda kullanın|  
|--------------|--------------|  
|Hizmet sürümü oluşturma|Bir hizmetin birden çok sürümünü desteketmeniz veya gelecekte güncelleştirilmiş bir hizmeti dağıtmanız gerekir|  
|Hizmet verileri bölümlendirme|Bir hizmeti birden fazla konakta bölümlemem gerekir|  
|Dinamik güncelleştirme|Değişen hizmet dağıtımlarını işlemek için çalışma zamanında yönlendirme mantığını dinamik olarak yeniden yapılandırmanız gerekir|  
|Noktalı|Birden çok uç noktaya bir ileti göndermeniz gerekir|  
|Protokol köprüleme|Bir Aktarım Protokolü üzerinden iletiler alırsınız ve hedef uç noktası farklı bir protokol kullanır|  
|Hata İşleme|Ağ kesintileri ve iletişim hatalarıyla esnekliği sağlamanız gerekir|  
  
> [!NOTE]
> Sunulan pek çok senaryo belirli iş gereksinimlerine veya işleme gereksinimlerine özgü olsa da, dinamik güncelleştirmeleri desteklemeyi planlama ve hata işlemeyi kullanma planlaması, çalışma zamanında yönlendirme mantığını değiştirmenize ve geçici ağ ve iletişim hatalarından kurtarılmasına olanak tanıdıklarından genellikle en iyi yöntem olarak kabul edilebilir.  
  
### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma  
 Bir hizmetin yeni bir sürümünü tanıtma sırasında, tüm istemciler yeni hizmete geçirilene kadar genellikle önceki sürümü korumanız gerekir. Bu özellikle, hizmetin gün, hafta veya hatta tamamlanma süresini geçen uzun süre çalışan bir işlemdir. Genellikle bunun için yeni hizmet için yeni bir uç nokta adresinin uygulanması gerekir, önceki sürüm için özgün uç nokta korunurken.  
  
 Yönlendirme hizmetini kullanarak, istemci uygulamalarından ileti almak için bir uç nokta sunabilir ve sonra her iletiyi ileti içeriğine göre doğru hizmet sürümüne yönlendirebilirsiniz. En temel uygulama, iletinin tarafından işlenmek üzere hizmet sürümünü belirten iletiye özel bir üst bilgi eklemeyi içerir. Yönlendirme hizmeti, özel üst bilgi varlığı için her iletiyi incelemek ve iletiyi uygun hedef uç noktaya yönlendirmek için XPathMessageFilter ' i kullanabilir.  
  
 Hizmet sürümü oluşturma yapılandırması oluşturmak için kullanılan adımlar için bkz. [nasıl yapılır: hizmet sürümü oluşturma](how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>Hizmet Verilerini Bölümlendirme  
 Dağıtılmış bir ortam tasarlarken, genellikle yüksek kullanılabilirlik sağlamak, tek bilgisayarlarda işlem yükünü azaltmak veya belirli bir ileti alt kümesi için adanmış kaynaklar sağlamak üzere birden çok bilgisayardaki işleme yükünü yaymak tercih edilir. Yönlendirme hizmeti adanmış bir yük dengeleme çözümünü değiştirmez, ancak içerik tabanlı yönlendirme gerçekleştirme özelliği, başka bir şekilde benzer iletileri belirli hedeflere yönlendirmek için kullanılabilir. Örneğin, belirli bir istemciden gelen iletileri diğer istemcilerden alınan iletilerden ayrı olarak işleme gereksinimine sahip olabilirsiniz.  
  
 Hizmet veri bölümleme yapılandırması oluşturmak için kullanılan adımlar için bkz. [nasıl yapılır: hizmet verileri bölümlendirme](how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Dinamik yönlendirme  
 Genellikle, bir hizmetin daha yeni bir sürümüne rota ekleme, yönlendirme ölçütlerini değiştirme veya hedef uç noktasını filtrenin yönlendirdiğini belirli bir ileti ile değiştirme gibi iş ihtiyaçlarını karşılamak için yönlendirme yapılandırmasını değiştirmek tercih edilir. Yönlendirme hizmeti, <xref:System.ServiceModel.Routing.RoutingExtension> çalışma zamanında yeni bir RoutingConfiguration sağlamanıza olanak sağlayan aracılığıyla bunu yapmanıza olanak sağlar. Yeni yapılandırma hemen yürürlüğe girer, ancak yalnızca Yönlendirme hizmeti tarafından işlenen yeni oturumları etkiler.  
  
 Dinamik yönlendirmeyi uygulamak için kullanılan adımlar için bkz. [nasıl yapılır: dinamik güncelleştirme](how-to-dynamic-update.md).
  
### <a name="multicast"></a>Noktalı  
 İletileri yönlendirçalışırken, genellikle her iletiyi belirli bir hedef uç noktaya yönlendirmenizi sağlar.  Ancak, bazen iletinin bir kopyasını birden çok hedef uç noktaya yönlendirmenize gerek olabilir. Çok noktaya yayın yönlendirmesi gerçekleştirmek için aşağıdaki koşulların doğru olması gerekir:  
  
- İstek-yanıt verme yöntemi, istek yanıtı olarak istemci uygulaması tarafından yalnızca bir yanıt alınabileceğinden, kanal şeklinin istek-yanıt (tek yönlü veya çift yönlü olabilir) olması gerekir.  
  
- İleti değerlendirilirken birden çok filtrenin **true** döndürmesi gerekir.  
  
 Bu koşullar karşılanıyorsa, doğru döndüren bir filtreyle ilişkilendirilen her bir hedef uç nokta iletinin bir kopyasını alır.  
  
### <a name="protocol-bridging"></a>Protokol köprüleme  
 Farklı SOAP protokolleri arasında iletileri yönlendirçalışırken, yönlendirme hizmeti iletiyi bir protokolden diğerine dönüştürmek için WCF API 'Lerini kullanır. Bu, yönlendirme hizmeti tarafından kullanıma sunulan hizmet uç noktaları, iletilerin yönlendirildiği istemci uç noktasından farklı bir protokol kullandığı zaman otomatik olarak gerçekleşir. Kullanımdaki protokoller standart değilse, bu davranışı devre dışı bırakmak mümkündür. Ancak, kendi köprü kodunuzu sağlamanız gerekir.
  
### <a name="error-handling"></a>Hata İşleme  
 Dağıtılmış bir ortamda, geçici ağ veya iletişim hatalarıyla karşılaşmanız yaygın olmayan bir durumdur. Yönlendirme hizmeti gibi bir aracı hizmeti olmadan, bu tür hataların işlenme yükü istemci uygulamasına düşer. İstemci uygulaması, ağ veya iletişim arızalarında veya alternatif konumlar hakkında yeniden denemek için belirli bir mantık içermiyorsa, Kullanıcı hedef hizmet tarafından başarıyla işlenmeden önce bir iletinin birden çok kez gönderilmesi gerektiği senaryolar ile karşılaşabilir. Bu, güvenilmez olarak algılanan gibi, müşterinin uygulamayla aynı olmasına neden olabilir.  
  
 Yönlendirme hizmeti, ağ veya iletişimle ilgili hatalarla karşılaşan iletiler için güçlü hata işleme özellikleri sağlayarak bu senaryoyu keşfetmeye çalışır. Olası hedef uç noktaların bir listesini oluşturarak ve bu listeyi her ileti filtresiyle ilişkilendirerek, tek bir olası hedefle karşılaşarak oluşan tek hata noktasını kaldırırsınız. Bir hata durumunda, yönlendirme hizmeti iletiyi teslim edilene, iletişim olmayan bir hata oluştuktan veya tüm uç noktaların tükenene kadar iletiyi listedeki bir sonraki uç noktaya teslim etmeye çalışır.  
  
 Hata işlemeyi yapılandırmak için kullanılan adımlar için bkz. [nasıl yapılır: hata işleme](how-to-error-handling.md).
  
### <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet Sürümü Oluşturma](how-to-service-versioning.md)  
  
 [Nasıl yapılır: Hizmet Verilerini Bölümlendirme](how-to-service-data-partitioning.md)  
  
 [Nasıl yapılır: Dinamik Güncelleme](how-to-dynamic-update.md)  
  
 [Nasıl yapılır: Hata İşleme](how-to-error-handling.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Tanıtımı](routing-introduction.md)
