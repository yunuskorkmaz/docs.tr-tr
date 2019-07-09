---
title: Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 3119f32d57cff01b81e4a8f4a3f3a571013300ea
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662782"
---
# <a name="routing-service"></a>Yönlendirme Hizmeti

Yönlendirme hizmeti bir ileti yönlendirici işlevi gören genel bir SOAP aracıdır. Yönlendirme hizmeti temel işlevlerini iletisini üst bilgi veya ileti gövdesi içindeki bir değere göre bir istemci uç noktası iletilmesi bir ileti veren ileti içeriği temel iletileri yönlendirmek yeteneğidir.

<xref:System.ServiceModel.Routing.RoutingService> Windows Communication Foundation (WCF) hizmet olarak uygulanan <xref:System.ServiceModel.Routing> ad alanı. İleti içeriği'da bir veya daha fazla istemci uç noktalarına her ileti yol tabanlı ve yönlendirme hizmeti iletilerini bir veya daha fazla hizmet uç noktalarını kullanıma sunar. Hizmet aşağıdaki özellikleri sağlar:

- İçerik tabanlı yönlendirme

  - Hizmet toplama

  - Hizmet sürümü oluşturma

  - Öncelikli yönlendirme

  - Dinamik yapılandırma

- Bağlantı protokolü

- SOAP işleme

- Gelişmiş hata işleme

- Yedekleme uç noktaları

Bir veya daha fazla bu hedeflere gerçekleştirir aracı bir hizmet oluşturmak mümkün olsa da, genellikle gibi bir uygulama belirli bir senaryoyu ya da çözüm bağlıdır ve kolayca yeni uygulamalar için uygulanamaz.

Yönlendirme hizmeti, WCF hizmeti ve kanal modelleri ile uyumlu olan ve iletilerin SOAP tabanlı içerik tabanlı yönlendirme gerçekleştirmenize olanak tanıyan bir genel, dinamik olarak yapılandırılabilir, takılabilir SOAP aracı sağlar.

> [!NOTE]
> Yönlendirme hizmeti, yönlendirme WCF REST Hizmetleri şu anda desteklemiyor.  REST çağrılarını yönlendirmek için kullanmayı <xref:System.Web.Routing> veya [uygulama isteği yönlendirme](https://go.microsoft.com/fwlink/?LinkId=164589).

## <a name="content-based-routing"></a>İçerik tabanlı yönlendirme

İçerik tabanlı yönlendirme iletisi içinde yer alan bir veya daha fazla değerlere göre bir ileti yolu yeteneğidir. Yönlendirme hizmeti, her bir ileti ve hedef uç nokta için ileti içeriği ve oluşturduğunuz yönlendirme mantığı göre yollar inceler. İçerik tabanlı yönlendirme, hizmet toplama, hizmet sürümü oluşturma ve öncelik yönlendirme için temel sağlar.

İçerik tabanlı yönlendirme uygulamak için yönlendirme hizmeti dayanan <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirilmesini iletileri içindeki belirli değerleri eşleştirmek için kullanılan uygulamaları. Varsa bir **MessageFilter** eşleşen bir ileti, ileti ile ilişkili hedef uç noktaya yönlendirilir **MessageFilter**.  İleti filtreleri filtre tablolarla birlikte gruplanır (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) karmaşık yönlendirme mantığı oluşturmak için. Örneğin, bir filtre tablo beş hedef uç noktaları yalnızca biri yönlendirilmesini iletileri neden beş birbirini dışlayan ileti filtreleri içerebilir.

Yönlendirme hizmeti yanı sıra içerik tabanlı yönlendirme gerçekleştirmek yönlendirme mantığı çalışma zamanında dinamik olarak güncelleştirmek için kullanılan mantıksal yapılandırmanıza olanak sağlar.

Aracılığıyla filtre tablolar halinde gruplandırmayı ileti filtreleri yönlendirme mantığı birden çok yönlendirme senaryoları gibi işlemeye izin veren oluşturulabilir:

- Hizmet toplama

- Hizmet sürümü oluşturma

- Öncelikli yönlendirme

- Dinamik yapılandırma

İleti filtreleri ve filtre tabloları hakkında daha fazla bilgi için bkz. [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md) ve [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).

### <a name="service-aggregation"></a>Hizmet toplama

İçerik tabanlı yönlendirme kullanarak dış istemci uygulamalarından iletileri alır ve ardından her ileti iletideki bir değere göre uygun iç uç nokta yönlendirir bir uç nokta üzerinden kullanıma sunabilirsiniz. Bu, çeşitli arka uç uygulamaları için belirli bir uç nokta sunmak ve çeşitli hizmetler uygulamanıza hesaba katacak şekilde sırasında bir uygulama uç noktası müşterilerinize sunmak için kullanışlıdır.

### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma

Çözümünüze yeni bir sürümüne geçirirken eski sürümü mevcut müşterilere paralel korumak zorunda kalabilirsiniz. Genellikle bu en yeni sürüme bağlanan istemciler farklı bir adres çözümü ile iletişim kurarken kullanmalıdır gerektirir. Yönlendirme hizmeti, çözümünüzün her iki sürümü de iletisinde bulunan sürüme özgü bilgileri temel alarak uygun çözüm yönlendirme iletileri tarafından hizmet veren bir hizmet uç noktası kullanıma sunmanıza olanak sağlar. Bu tür uygulaması örneği için bkz. [nasıl yapılır: Hizmet sürümü oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).

### <a name="priority-routing"></a>Öncelikli yönlendirme

Bir hizmet birden çok istemci için sağlarken, diğer istemciler ayrı olarak işlenmek üzere bu iş ortaklarının sunduğu tüm verileri gerektiren bazı iş ortaklarıyla bir hizmet düzeyi sözleşmesi (SLA) olabilir. İletinin müşteriye özgü bilgileri bakan bir filtre kullanarak belirli iş ortaklarından iletileri kendi SLA gereksinimlerini karşılamak için oluşturulan bir uç noktaya kolayca yönlendirebilirsiniz.

## <a name="dynamic-configuration"></a>Dinamik yapılandırma

Burada iletileri herhangi bir hizmet kesinti işlenmesi gereken, görev açısından kritik sistemlerinin desteklemek için çalışma zamanında bileşenler içerisinden sistem yapılandırmasını değiştirmek için önemlidir. Bu gereksinimi desteklemek için yönlendirme hizmeti sağlar. bir <xref:System.ServiceModel.IExtension%601> uygulaması <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasının dinamik güncelleştirme izin verir.

Dinamik yönlendirme hizmeti yapılandırması hakkında daha fazla bilgi için bkz. [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="protocol-bridging"></a>Bağlantı protokolü

Aracı senaryolarda zorlukların iç Uç noktalara farklı taşıma veya SOAP sürümü gereksinimlerine iletilerin alınıp alınmadığını uç nokta olabilir biridir. Bu senaryoyu desteklemek için yönlendirme hizmeti için SOAP ileti işleme gibi protokolleri arasında köprü olabilir <xref:System.ServiceModel.Channels.MessageVersion> hedef uç nokta tarafından gerekli. Başka bir dış iletişimi için kullanılabilse de bu şekilde, bir protokol dahili iletişim için kullanılabilir.

Farklı aktarımları ile uç noktalar arasında iletileri yönlendirme desteklemek için benzer olmayan protokolleri arasında köprü kuracak şekilde hizmet sağlayan sistem tarafından sağlanan bağlamalar yönlendirme hizmeti kullanır. Yönlendirme hizmeti tarafından kullanıma sunulan hizmet uç noktası iletileri yönlendirilir istemci uç noktalarını değerinden farklı bir protokol kullandığında otomatik olarak gerçekleşir.

## <a name="soap-processing"></a>SOAP işleme

Ortak bir yönlendirme gereksinim farklı SOAP gereksinimlerine sahip uç noktaları arasında iletileri yönlendirmek yeteneğidir. Bu gereksinimi desteklemek için yönlendirme hizmeti sağlar. bir <xref:System.ServiceModel.Routing.SoapProcessingBehavior> otomatik olarak yeni bir oluşturan **MessageVersion** karşılayan gereksinimleri hedef uç nokta ileti yönlendirilmeden önce. Bu davranış da yeni bir oluşturur **MessageVersion** emin olmak için istekte bulunan istemci uygulamaya döndürmeden önce herhangi bir yanıt iletisi için **MessageVersion** yanıtı ile eşleşir özgün istek.

SOAP işleme hakkında daha fazla bilgi için bkz. [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="error-handling"></a>Hata İşleme

Ağ iletişimini kullanan dağıtılmış hizmetlerin oluşan bir sistemde, bu iletişim geçici ağ hatalarını ertelerler sisteminiz içinde sağlamak önemlidir.  Yönlendirme hizmeti, aksi takdirde bir hizmet kesintisine neden olabilir birçok iletişim hatası senaryolarında işlemeye izin veren hata işleme uygular.

Yönlendirme hizmeti ile karşılaşırsa, bir <xref:System.ServiceModel.CommunicationException> bir ileti gönderilmeye çalışılırken hata işleme gerçekleşir.  Bu özel durumlar genellikle gibi tanımlı istemci uç noktası ile iletişim kurmaya çalışılırken bir sorunla karşılaşıldı gösterir bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Hata işleme kodu ayrıca catch ve ne zaman göndermeyi yeniden deneme girişimi bir **TimeoutException** gerçekleşir, türünden türetilmediğinden başka bir genel özel durum olduğu **CommunicationException**.

Hata işleme hakkında daha fazla bilgi için bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="backup-endpoints"></a>Yedekleme uç noktaları

Hedef istemci uç noktaları filtre tablodaki her filtre tanımıyla ilişkili ek olarak, ileti için bir iletim hatası durumunda yönlendirilecek yedekleme uç noktaları listesi oluşturabilirsiniz. Bir hata oluşur ve yedekleme listesini filtre girişini tanımlanır, yönlendirme hizmeti listesinde tanımlanan ilk uç nokta ileti göndermek dener. Bu hizmet iletim girişimi başarısız sonraki uç nokta deneyin ve bu işlem iletim denemesi başarılı olana kadar devam iletim olmayan ilgili bir hata veya yedekleme listesindeki tüm uç noktaları bir iletim hatası döndürmüş döndürür.

Yedekleme uç noktaları hakkında daha fazla bilgi için bkz. [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md) ve [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).

## <a name="streaming"></a>Akış

Akış desteklemek için bağlama ayarlarsanız, yönlendirme hizmeti başarıyla iletileri akışını yapabilirsiniz.  Ancak, bazı koşullar altında iletileri arabelleğe gerekebilir vardır:

- Çok noktaya yayın (ek ileti kopya oluşturmak için arabellek)

- Yük devretme (arabellek yedek gönderilecek iletinin gerekiyor durumunda)

- System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly false (filtreler gövdesi inceleyebilmeniz adına bir MessageBuffer ile MessageFilterTable sunmak için arabellek)

- Dinamik yapılandırma

## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
- [Anlaşmaları Yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md)
- [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)
