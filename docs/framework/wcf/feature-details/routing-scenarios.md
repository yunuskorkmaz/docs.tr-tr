---
title: "Yönlendirme Senaryoları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ef101a9a5f78e1b85ac7cb983b4766088b83317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="routing-scenarios"></a>Yönlendirme Senaryoları
Yönlendirme hizmeti yüksek oranda özelleştirilebilir olsa da, verimli yönlendirme mantığı yeni bir yapılandırma sıfırdan oluştururken tasarlamak için bir sınama olabilir.  Ancak, çoğu yönlendirme hizmeti yapılandırması izleyin birçok yaygın senaryolar vardır. Bu senaryolar belirli yapılandırmanızı doğrudan geçerli olmayabilir, ancak bu senaryoları işlemek için yönlendirme hizmeti nasıl yapılandırılabilir anlama, yönlendirme hizmeti anlaşılmasına yardımcı olur.  
  
## <a name="common-scenarios"></a>Yaygın senaryolar  
 En temel yönlendirme hizmeti için kullanılır istemci uygulamaları için kullanıma sunulan uç noktaların sayısını azaltmak için birden çok hedef uç nokta toplamak ve her iletinin doğru hedefine yönlendirmek için ileti filtreleri kullanın. Belirli bir hizmeti tarafından işlenen veya gerekir öncelik belirli bir kaynaktan iletilerinin işlenmesini sağlayarak gibi rasgele iş gereksinimlerini temel bir ileti türü gibi mantıksal veya fiziksel işleme gereksinimlerine göre iletileri yönlendirilebilir. Aşağıdaki tabloda bazı yaygın senaryolar ve bunlar karşılaştığında yer almaktadır:  
  
|Senaryo|Şu durumlarda kullanın|  
|--------------|--------------|  
|Hizmet sürümü oluşturma|Bir hizmet birden fazla sürümünü desteklemesi gerekir ya da güncelleştirilmiş bir hizmet gelecekte dağıtma|  
|Hizmet verilerini bölümlendirme|Bir hizmet birden çok konak genelinde bölüm|  
|Dinamik güncelleştirme|Yönlendirme mantığı değişen hizmet dağıtımları işlemek için çalışma zamanında dinamik olarak yeniden yapılandırmanız gerekir|  
|Çok noktaya yayın|Birden çok uç nokta için bir ileti göndermesi gerekir|  
|Protokol köprü oluşturma|Bir aktarım protokolü üzerinden iletileri almasına ve farklı bir protokol için hedef uç nokta kullanır|  
|Hata İşleme|Ağ kesintileri ve iletişim hatası esnekliği sağlamanız gerekir|  
  
> [!NOTE]
>  Çalışma zamanında yönlendirme mantığı değiştirmenize izin sunulan senaryoları belirli iş ihtiyaçlarınızı karşılamak için özgü ya da işleme gereksinimlerini, dinamik güncelleştirmeleri destekleyecek şekilde planlama ve hata işleme kullanan genellikle için en iyi yöntemler değerlendirilmesi ve geçici ağ ve iletişim hatalarından kurtarın.  
  
### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma  
 Tüm istemcilerin yeni hizmet geçti kadar bir hizmetin yeni bir sürümü uygulandığında, önceki sürüm genellikle bulundurmanız gerekir. Gün, hafta veya ay bile tamamlanması için gereken bir uzun süre çalışan işlemin hizmete ise, bu özellikle önemlidir. Genellikle bu yeni hizmet için yeni bir uç nokta adresi özgün uç nokta önceki sürümü için korurken uygulama gerektirir.  
  
 Yönlendirme hizmeti kullanarak, istemci uygulamalarından iletileri almasına ve ileti içeriğine göre doğru hizmet sürümüne her ileti yönlendirmek için bir uç nokta getirebilir. En temel uygulaması tarafından işlenmek üzere iletisidir hizmetinin sürümü bildiren ileti için bir özel üst bilgi eklenmesi gerektirir. Yönlendirme hizmeti XPathMessageFilter her ileti için özel üstbilgi varlığını inceleyin ve uygun hedef uç noktasına ileti yönlendirmek için kullanabilirsiniz.  
  
 Bir hizmet sürümü oluşturma yapılandırması oluşturmak için kullanılan adımlar için bkz: [nasıl yapılır: Hizmet sürümü oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md). Özel bir üstbilgisi temelinde iletileri yönlendirmek için XPathMessageFilter kullanma örneği için bkz: [Gelişmiş filtreler](../../../../docs/framework/wcf/samples/advanced-filters.md) örnek.  
  
### <a name="service-data-partitioning"></a>Hizmet verilerini bölümlendirme  
 Dağıtılmış bir ortama tasarlarken, genellikle yüksek kullanılabilirlik sağlamak için tek tek bilgisayarlarda işleme yükünü azaltmak için veya belirli bir alt için ayrılmış kaynakları sağlamak için işleme yükünü birden fazla bilgisayara yaymak için tercih edilir iletileri. Yönlendirme hizmeti adanmış bir yük dengeleme çözümü değiştirmez, ancak içerik tabanlı yönlendirme gerçekleştirme yeteneğini belirli hedeflere aksi benzer iletileri yönlendirmek için kullanılabilir. Örneğin, ayrı ayrı diğer istemcilerinden alınan iletilerin belirli bir istemciden gelen iletilerini işlemek için gerekli olabilir.  
  
 Yapılandırma bölümleme hizmet verileri oluşturmak için kullanılan adımlar için bkz: [nasıl yapılır: hizmet verilerini bölümlendirme](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md). URL ve özel üstbilgi göre bölüm verileri filtrelerini kullanma örneği için bkz: [Gelişmiş filtreler](../../../../docs/framework/wcf/samples/advanced-filters.md) örnek.  
  
### <a name="dynamic-routing"></a>Dinamik yönlendirme  
 Genellikle bir rota filtre yönlendirir belirli bir ileti yönlendirme ölçütlerini değiştirmek veya hedef uç nokta değiştirme hizmetinin daha yeni bir sürüme ekleme gibi değişen iş gereksinimlerini karşılamak için yönlendirme yapılandırmasını değiştirmek için tercih edilir. Yönlendirme hizmeti aracılığıyla bunu sayesinde <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanı sırasında yeni bir RoutingConfiguration sağlamak sağlar. Yeni yapılandırma hemen etkili olur, ancak yalnızca yönlendirme hizmeti tarafından işlenen tüm yeni oturumlar etkiler.  
  
 Dinamik yönlendirme uygulamak için kullanılan adımlar için bkz: [nasıl yapılır: dinamik güncelleştirme](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md). Dinamik yönlendirme kullanmanın bir örnek için bkz [dinamik yeniden yapılandırma](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md) örnek.  
  
### <a name="multicast"></a>Çok noktaya yayın  
 Genellikle iletilerin yönlendirme, belirli bir hedef uç noktasına her ileti yönlendirme.  Ancak, bazen iletinin bir kopyasını birden çok hedef Uç noktalara yönlendirmek gerekebilir. Çok noktaya yayın yönlendirme gerçekleştirmek için aşağıdaki koşulların doğru olması gerekir:  
  
-   (Ancak tek yönlü veya çift yönlü olabilir) istek-yanıt yalnızca bir yanıt isteğine yanıt olarak istemci uygulaması tarafından alınabilir olması zorunlu tutulmuştur çünkü kanal şekli istek-yanıt olması gerekir.  
  
-   Birden çok filtre döndürmelidir **true** ileti değerlendirirken.  
  
 Bu koşullar karşılanıyorsa true değerini döndürür bir filtre ile ilişkili her hedef uç nokta iletinin kopyasını alır.  
  
### <a name="protocol-bridging"></a>Protokol köprü oluşturma  
 İletileri farklı SOAP protokolleri arasında yönlendirme, yönlendirme hizmeti WCF API'leri ileti bir protokolünden dönüştürmek için kullanır. Bu, otomatik olarak zaman Hizmeti uç iletileri yönlendirilir istemci uç daha farklı bir protokol yönlendirme hizmeti kullanımına sunulan oluşur. Kullanılan protokoller standart değilse bu davranışı devre dışı bırakmak mümkündür; Ancak, daha sonra kendi kod köprüleme sağlamanız gerekir.  
  
 biçimindeki telefon numarasıdır. Protokolleri arasında iletileri çevirmek için yönlendirme hizmeti kullanarak bir örnek için bkz: [köprü oluşturma ve hata işleme](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) örnek.  
  
### <a name="error-handling"></a>Hata İşleme  
 Dağıtılmış bir ortamda, geçici ağ ya da iletişim hatalarıyla karşılaşırsanız sık karşılaşılan bir durum değil. Yönlendirme hizmeti gibi bir aracı hizmeti olmadan istemci uygulaması gibi hatalarını işleme yükünü döner. İstemci uygulaması ağ veya iletişim hatası ve alternatif konumlar bilgisi durumunda yeniden denemek için belirli mantığı içermiyorsa, kullanıcı başarıyla önce burada bir ileti birden çok kez gönderilmelidir senaryoları karşılaşabilirsiniz Hedef hizmeti tarafından işlenen. Olarak güvenilmeyen algılanabilir gibi bu uygulama müşteri memnuniyetsizlik neden olabilir.  
  
 Bu senaryo için ağ veya iletişim ile ilgili hataları karşılaşmanız iletileri işleme özellikleri sağlam hata sağlayarak sorunu gidermek yönlendirme hizmeti çalışır. Olası hedef uç noktaları listesi oluşturma ve bu listede her ileti Filtresi ile ilişkilendirme tek tek olası hedef sağlayarak sonucunda oluşan hata noktası kaldırın. Bir arıza olması durumunda, yönlendirme hizmeti iletişimi olmayan hatası oluştuğunda, ileti taşınana veya tüm uç noktaları tüketmiş kadar sonraki uç listesinde ileti teslim dener.  
  
 Hata işleme yapılandırmak için kullanılan adımlar için bkz: [nasıl yapılır: hata işleme](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md). Hata işleme uygulama örneği için bkz: [köprü oluşturma ve hata işleme](../../../../docs/framework/wcf/samples/bridging-and-error-handling.md) ve [Gelişmiş hata işleme](../../../../docs/framework/wcf/samples/advanced-error-handling.md) örnekleri.  
  
### <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet Sürümü Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Nasıl yapılır: Hizmet Verilerini Bölümlendirme](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Nasıl yapılır: Dinamik Güncelleme](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Nasıl yapılır: Hata İşleme](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
