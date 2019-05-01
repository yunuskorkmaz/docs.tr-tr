---
title: Yönlendirme Senaryoları
ms.date: 03/30/2017
helpviewer_keywords:
- rounting [WCF], scenarios
ms.assetid: ec22f308-665a-413e-9f94-7267cb665dab
ms.openlocfilehash: fa5d588211cfe40cde9e9db3161a931e3287cd39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991068"
---
# <a name="routing-scenarios"></a>Yönlendirme Senaryoları
Yönlendirme hizmeti yüksek oranda özelleştirilebilir olsa da, bunu yeni bir yapılandırma sıfırdan oluştururken, verimli yönlendirme mantığı tasarlamak için bir mücadele haline gelebilir.  Ancak, çoğu yönlendirme hizmeti yapılandırma izleyin birçok yaygın senaryo vardır. Bu senaryolar belirli yapılandırmanızı doğrudan geçerli değil. ancak, yönlendirme hizmeti bu senaryolar işlemek için nasıl yapılandırılabileceğini anlama, yönlendirme hizmeti anlaşılmasına yardımcı olur.  
  
## <a name="common-scenarios"></a>Yaygın senaryolar  
 En temel kullanımı yönlendirme hizmeti, birden çok hedef uç noktaları için istemci uygulamaları kullanıma sunulan uç noktaların sayısını azaltmak için toplama ve ardından her ileti için doğru hedef yolu için ileti filtreleri kullanın. İletileri gereken belirli bir hizmeti tarafından işlenen veya belirli bir kaynaktan gelen iletileri öncelik işlenmesini sağlamak gibi rastgele işletme ihtiyaçlarını temel türden bir ileti gibi mantıksal veya fiziksel işleme gereksinimlerine göre yönlendirilebilir. Aşağıdaki tablo bazı yaygın senaryolar ve bunlar karşılaştığında listeler:  
  
|Senaryo|Şu durumlarda kullanın|  
|--------------|--------------|  
|Hizmet sürümü oluşturma|Bir hizmet birden çok sürümünü destekliyor olması veya güncelleştirilmiş bir hizmet gelecekte dağıtma|  
|Hizmet verilerini bölümlendirme|Birden çok konak genelinde hizmet bölümleme|  
|Dinamik güncelleştirme|Yönlendirme mantığı değişen hizmet dağıtımları işlemek için çalışma zamanında dinamik olarak yeniden yapılandırmanız gerekir|  
|Çok noktaya yayın|Birden fazla uç nokta için bir ileti gönderin|  
|Bağlantı protokolü|Bir aktarım protokolü üzerinden ileti alma ve farklı bir protokol hedef uç nokta kullanır|  
|Hata İşleme|Ağ kesintilerine ve iletişim hatalarına dayanıklılık sağlamanız gerekir|  
  
> [!NOTE]
>  Çalışma zamanında yönlendirme mantığı değiştirmenize izin sunulan senaryoların çoğunun belirli iş ihtiyaçlarınızı karşılamak için belirli ya da işleme gereksinimlerine, dinamik güncelleştirmeleri desteklemek planlama ve hata işleme yararlanarak olabilir, genellikle en iyi yöntemler göz önünde bulundurulması ve geçici ağ ve iletişimi hatalardan kurtarın.  
  
### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma  
 Tüm istemcilerin yeni hizmete geçirileceğini kadar bir hizmetin yeni bir sürüm ile tanışın, önceki sürümü genellikle sürdürmeniz gerekir. Günler, haftalar veya aylar bile tamamlamak için gereken bir uzun süre çalışan işlem hizmeti ise, bu özellikle önemlidir. Genellikle bu yeni hizmet için yeni bir uç nokta adresi önceki sürümü için özgün uç nokta korurken uygulama gerektirir.  
  
 Yönlendirme hizmetini kullanarak, istemci uygulamalarından iletileri almak ve ardından her ileti, ileti içeriğine göre doğru hizmet sürümüne yönlendirmek için bir uç nokta üzerinden kullanıma sunabilirsiniz. En temel uygulama tarafından işlenmek üzere iletidir hizmetinin sürümü belirten ileti bir özel üst bilgi eklemeyi içerir. Yönlendirme hizmeti, her ileti için özel üst bilgi varlığını denetlemek ve uygun hedef uç noktasına ileti yönlendirme XPathMessageFilter kullanabilirsiniz.  
  
 Bir hizmeti sürüm yapılandırması oluşturmak için kullanılan adımları için bkz [nasıl yapılır: Hizmet sürümü oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).
  
### <a name="service-data-partitioning"></a>Hizmet Verilerini Bölümlendirme  
 Dağıtılmış bir ortama tasarlarken, genellikle yüksek kullanılabilirlik sağlamak için tek tek bilgisayarlarda işleme yükünü azaltın ya da belirli bir alt kümesi için ayrılmış kaynak sağlamak için işleme yükünü birden fazla bilgisayara yaymak için tercih edilir iletileri. Yönlendirme hizmeti, bir adanmış yük dengeleme çözümü değiştirmez, ancak içerik tabanlı yönlendirme gerçekleştirme becerisi, belirli hedeflere aksi benzer iletileri yönlendirmek için kullanılabilir. Örneğin, ayrı olarak diğer istemcilerden alınan iletileri belirli bir istemciden iletilerini işlemek için bir gereksinim olabilir.  
  
 Yapılandırma bölümleme verileri bir hizmet oluşturmak için kullanılan adımları için bkz [nasıl yapılır: Hizmet verilerini bölümlendirme](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md).  
  
### <a name="dynamic-routing"></a>Dinamik yönlendirme  
 Genellikle bir yol filtresi yönlendirir, belirli bir ileti yönlendirme ölçütlerini değiştirmek ya da hedef bitiş noktasını değiştirerek bir hizmeti daha yeni bir sürümüne ekleme gibi değişen iş gereksinimlerini karşılamak için yönlendirme yapılandırmasını değiştirmek için tercih edilir. Yönlendirme hizmeti aracılığıyla bunu sağlar <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanı sırasında yeni bir RoutingConfiguration sağlamak sağlar. Yeni yapılandırma hemen etkili olur, ancak yalnızca yönlendirme hizmeti tarafından işlenen tüm yeni oturumlar etkiler.  
  
 Dinamik yönlendirme uygulamak için kullanılan adımları için bkz. [nasıl yapılır: Dinamik güncelleştirme](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md).
  
### <a name="multicast"></a>Çok noktaya yayın  
 Genellikle ileti yönlendirme, belirli bir hedef uç noktasına her ileti yönlendirme.  Bununla birlikte, iletinin bir kopyasını birden çok hedef Uç noktalara yönlendirmek zaman zaman gerekebilir. Çok noktaya yayın yönlendirme gerçekleştirmek için aşağıdaki koşulların doğru olması gerekir:  
  
- (Bu tek yönlü veya çift yönlü olabilir, ancak) kanal şekli yalnızca bir yanıt isteğine yanıt olarak istemci uygulaması tarafından alınan, istek-yanıt taahhütlerin olduğundan istek-yanıt olmamalıdır.  
  
- Birden çok filtre döndürmelidir **true** ileti değerlendirirken.  
  
 Bu koşullar karşılanıyorsa true döndüren bir filtre ile ilişkili her bir hedef uç noktasının iletinin bir kopyasını alır.  
  
### <a name="protocol-bridging"></a>Bağlantı protokolü  
 Benzer olmayan SOAP protokollerini arasında iletileri yönlendirme, yönlendirme hizmeti ileti bir protokolden dönüştürmek için WCF API'lerini kullanır. Hizmet uç noktalarına yönlendirme hizmetini kullanarak iletileri yönlendirilir istemci uç noktalarına değerinden farklı bir protokol ne zaman kullanıma otomatik olarak gerçekleşir. Standart protokoller kullanımda değilse, bu davranışı devre dışı bırakmak mümkündür; Ancak, ardından kendi kod köprüleme sağlamalısınız.
  
### <a name="error-handling"></a>Hata İşleme  
 Dağıtılmış bir ortamda geçici ağ ya da iletişim hatalarıyla karşılaşırsanız sık karşılaşılan bir durum değil. Yönlendirme hizmeti gibi bir aracı hizmeti olmadan da bu tür hataları işleme yükünü istemci uygulamasında döner. İstemci uygulaması belirli mantıksal ağ veya iletişim hatası ve alternatif konum bilgisine olması durumunda yeniden deneyecek şekilde içermiyorsa, kullanıcı başarıyla önce burada bir ileti birden çok kez gönderilmelidir durumlarla karşılaşabilirsiniz Hedef hizmet tarafından işlenir. Güvenilir olarak algılanabilir olarak bu uygulama ile müşteri memnuniyetsizliğine neden olabilir.  
  
 Yönlendirme hizmeti sağlam hata işleme özellikleri için ağ veya iletişim ile ilgili hataları karşılaşmanız iletileri sağlayarak bu senaryoyu çözmek çalışır. Olası hedef uç noktaları listesi oluşturma ve bu liste her ileti Filtresi ile ilişkilendirerek, tek tek bir olası hedef sağlayarak sonucunda hata noktasını kaldırın. Bir hata olması durumunda, yönlendirme hizmeti, tüm uç noktalar tüketmiş ya da olmayan bir iletişim hatası oluştuğunda hata, ileti taşınana kadar listedeki sonraki uç nokta için ileti teslim dener.  
  
 Hata işleme yapılandırmak için kullanılan adımları için bkz. [nasıl yapılır: Hata işleme](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md).
  
### <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Hizmet sürümü oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md)  
  
 [Nasıl yapılır: Hizmet verilerini bölümlendirme](../../../../docs/framework/wcf/feature-details/how-to-service-data-partitioning.md)  
  
 [Nasıl yapılır: Dinamik güncelleştirme](../../../../docs/framework/wcf/feature-details/how-to-dynamic-update.md)  
  
 [Nasıl yapılır: Hata işleme](../../../../docs/framework/wcf/feature-details/how-to-error-handling.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
