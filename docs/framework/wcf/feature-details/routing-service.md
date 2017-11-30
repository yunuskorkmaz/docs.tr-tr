---
title: "Yönlendirme Hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a4f58c5124e229f1692dabbb0abded0e21a346f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="routing-service"></a>Yönlendirme Hizmeti
Yönlendirme iletisi yönlendirici olarak davranan genel bir SOAP aracı hizmetidir. Yönlendirme hizmeti çekirdek işlevselliğini iletisini üstbilgisinde veya ileti gövdesi içinde bir değere göre bir istemci uç noktası iletilmesi için bir ileti verir ileti içeriği göre iletileri yönlendirmek için yeteneğidir.  
  
 <xref:System.ServiceModel.Routing.RoutingService> Olarak uygulanan bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti <xref:System.ServiceModel.Routing> ad alanı. Yönlendirme hizmeti iletilerini bir veya daha fazla hizmet uç noktaları kullanıma sunar ve ardından yollar her ileti bir veya daha fazla istemci uç noktaları için ileti içeriğine göre. Hizmet aşağıdaki özellikleri sağlar:  
  
-   İçerik tabanlı yönlendirme  
  
    -   Hizmet toplama  
  
    -   Hizmet sürümü oluşturma  
  
    -   Öncelik yönlendirme  
  
    -   Dinamik yapılandırma  
  
-   Protokol köprü oluşturma  
  
-   SOAP işleme  
  
-   Gelişmiş hata işleme  
  
-   Yedekleme uç noktaları  
  
 Bir veya daha fazla bu hedefleri gerçekleştirir bir aracı hizmeti oluşturmak mümkün olsa da, genellikle gibi bir uygulama belirli bir senaryoyu ya da çözüm bağlıdır ve kolayca yeni uygulamalara uygulanamaz.  
  
 Yönlendirme hizmeti ile uyumlu bir genel, dinamik olarak yapılandırılabilir, takılabilir SOAP aracıyı sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ve kanal modeller ve SOAP tabanlı iletilerin içerik tabanlı yönlendirme gerçekleştirmenizi sağlar.  
  
> [!NOTE]
>  Yönlendirme yönlendirme hizmeti şu anda desteklemiyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST Hizmetleri.  REST çağrılarını yönlendirmek için kullanmayı <xref:System.Web.Routing> veya [uygulama isteği yönlendirme](http://go.microsoft.com/fwlink/?LinkId=164589) (http://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>İçerik tabanlı yönlendirme  
 İçerik tabanlı yönlendirme iletisi içinde yer alan bir veya daha fazla değerlere göre bir ileti yönlendirmek için yeteneğidir. Yönlendirme hizmeti her ileti ve hedef uç nokta için ileti içeriği ve oluşturduğunuz yönlendirme mantığı göre yolları olup olmadığını denetler. İçerik tabanlı yönlendirme temel hizmet toplama, hizmet sürümü oluşturma ve öncelik yönlendirme sağlar.  
  
 İçerik tabanlı yönlendirme uygulamak için yönlendirme hizmeti dayanan <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirilmesi için iletilerini içindeki belirli değerleri eşleştirmek için kullanılan uygulamaları. Varsa bir **MessageFilter** bir ileti, ileti ile ilişkili hedef uç noktasına yönlendirilir eşleşmeleri **MessageFilter**.  İleti filtreleri birlikte filtre tablolara gruplandırılmış (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) karmaşık yönlendirme mantığı oluşturulamadı. Örneğin, bir filtre tablo beş hedef uç noktaları yalnızca biri yönlendirilecek iletileri neden beş birbirini dışlayan ileti filtreleri içerebilir.  
  
 Yönlendirme hizmeti yanı sıra içerik tabanlı yönlendirme gerçekleştirmek yönlendirme mantığı çalışma zamanında dinamik olarak güncelleştirmek için kullanılan mantığı yapılandırmanıza olanak sağlar.  
  
 Gruplandırması ileti filtreleri aracılığıyla filtre tablolara, birden çok yönlendirme senaryoları gibi işlemeye izin veren yönlendirme mantığı oluşturulabilir:  
  
-   Hizmet toplama  
  
-   Hizmet sürümü oluşturma  
  
-   Öncelik yönlendirme  
  
-   Dinamik yapılandırma  
  
 İleti filtreleri ve filtre tabloları hakkında daha fazla bilgi için bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md) ve [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Hizmet toplama  
 İçerik tabanlı yönlendirme kullanarak dış istemci uygulamalarından iletilerini alan ve her ileti, ileti içinde bir değere göre uygun dahili uç noktayı yönlendirir bir uç nokta getirebilir. Bu, belirli bir uç arka uç uygulamaları çeşitli sunmak için ve ayrıca çeşitli hizmetlere uygulamanıza Finansman sırasında bir uygulama uç nokta müşterilere sunmak için kullanışlıdır.  
  
### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma  
 Çözümünüzü yeni bir sürüme geçirirken, eski sürüm varolan müşteriye hizmet vermek için paralel korumak olabilir. Genellikle bu sürüme bağlanan istemciler farklı bir adres çözümü ile iletişim kurarken kullanmalısınız gerektirir. Yönlendirme hizmeti Yönlendirme ileti iletideki sürüme özgü bilgileri temel alarak uygun çözüm için çözümünüzün her iki sürümü hizmet veren bir hizmet uç noktası kullanıma izin verir. Bu tür bir uygulama örneği için bkz: [nasıl yapılır: Hizmet sürümü oluşturma](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Öncelik yönlendirme  
 Bir hizmet birden çok istemci sağlarken, diğer istemciler ayrı olarak işlenmek üzere bu iş ortaklarının tüm veriler gerektiren bazı iş ortakları ile hizmet düzeyi sözleşmesi (SLA) olabilir. İletideki müşteriye özgü bilgileri arar bir filtre kullanarak belirli iş ortakları iletilerden SLA gereksinimleri karşılamak için oluşturulan bir uç nokta için kolayca yönlendirebilirsiniz.  
  
## <a name="dynamic-configuration"></a>Dinamik yapılandırma  
 Burada iletileri tüm hizmet kesinti olmadan işlenmesi gereken, kritik sistemler desteklemek için sistemi içinde bileşenleri yapılandırmasını çalışma zamanında değiştirebilmek için önemlidir. Bu gereksinimi desteklemek için yönlendirme hizmeti sağlayan bir <xref:System.ServiceModel.IExtension%601> uygulaması, <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasının dinamik güncelleştirme izin verir.  
  
 Dinamik yönlendirme hizmeti yapılandırması hakkında daha fazla bilgi için bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Protokol köprü oluşturma  
 Ara senaryolarda zorluklar iç uç farklı taşıma veya SOAP sürüm gereksinimlerini ileti üzerinde alındığında uç nokta değerinden olabilir biridir. Bu senaryoyu desteklemek için yönlendirme hizmeti SOAP iletisi işleme dahil protokoller arasında köprü olabilir <xref:System.ServiceModel.Channels.MessageVersion> hedef uç tarafından gerekli. Başka bir dış iletişimi için kullanılabilmesine karşın bu şekilde, bir protokol iç iletişim için kullanılır.  
  
 İletileri farklı taşımalar ile uç noktalar arasında yönlendirme desteklemek için farklı protokoller birleştirmesi hizmetini etkinleştirme sistem tarafından sağlanan bağlamalar yönlendirme hizmeti kullanır. Yönlendirme hizmeti tarafından sunulan hizmet uç noktası iletileri yönlendirilir istemci uç noktaları daha farklı bir protokol kullandığında otomatik olarak gerçekleşir.  
  
## <a name="soap-processing"></a>SOAP işleme  
 Ortak bir yönlendirme gereksinim farklı SOAP gereksinimleriyle uç noktalar arasında iletileri yönlendirmek için özelliğidir. Bu gereksinimi desteklemek için yönlendirme hizmeti sağlayan bir <xref:System.ServiceModel.Routing.SoapProcessingBehavior> otomatik olarak yeni bir oluşturan **MessageVersion** karşılayan hedef uç nokta gereksinimlerini ileti yönlendirilmeden önce. Bu davranış da yeni bir oluşturur **MessageVersion** emin olmak için istekte bulunan istemci uygulamaya dönmeden önce herhangi bir yanıt iletisi için **MessageVersion** yanıtını sürümüyle eşleşen özgün istek.  
  
 SOAP işleme hakkında daha fazla bilgi için bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Hata İşleme  
 Ağ iletişimini kullanan dağıtılmış hizmet oluşan bir sistemde, bu iletişimler sisteminiz olan geçici ağ hatalarını dirençli içinde sağlamak önemlidir.  Yönlendirme hizmeti, aksi takdirde bir hizmet kesintisine neden olabilir birçok iletişim hatası senaryoları işlemeye izin veren hata işleme uygular.  
  
 Yönlendirme hizmeti karşılaşırsa bir <xref:System.ServiceModel.CommunicationException> bir ileti göndermeye çalışırken hata işleme gerçekleşir.  Bu özel durumlar gibi tanımlanmış istemci uç noktası ile iletişim kurmaya çalışırken bir sorunla karşılaşıldı genellikle belirtmek bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Hata işleme kodu da yakalamak ve ne zaman göndermeyi yeniden deneme girişimi bir **TimeoutException** oluşur, türetilmedi başka bir ortak özel durumu olan **CommunicationException**.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]hata işleme, bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Yedekleme uç noktaları  
 Her filtre tanımını filtre tablosundaki ile ilişkili hedef istemci uç noktaları ek olarak, ileti için bir iletim hatası durumunda yönlendirilir yedekleme uç noktaları listesi oluşturabilirsiniz. Bir hata oluşur ve yedekleme listesini filtre girişi için tanımlanan, yönlendirme hizmeti listesinde tanımlı Birinci uç nokta ileti göndermeye çalışacak. Bu iletim girişimi başarısız oldu, hizmet sonraki endpoint deneyin ve bu işlem iletim denemesi başarılı olana kadar devam, iletim olmayan ilgili hata veya yedekleme listesindeki tüm uç noktaları bir iletim hatası döndürmüş döndürür.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Yedekleme uç noktaları, bkz: [yönlendirme giriş](../../../../docs/framework/wcf/feature-details/routing-introduction.md) ve [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>Akış  
 Akış desteklemek için bağlama ayarlarsanız, yönlendirme hizmeti başarıyla iletileri akışını sağlayabilirsiniz.  Ancak, bazı koşullar altında iletilerini arabelleğe gerekebilir vardır:  
  
-   Çok noktaya yayın (ek ileti kopya oluşturmak için arabellek)  
  
-   Yük devretme (arabellek durumda bir yedekleme gönderilecek ileti gerekiyor)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly değer false (filtreleri gövdesi inceleyebilirsiniz böylece bir MessageBuffer ile MessageFilterTable sunmak için arabellek)  
  
-   Dinamik yapılandırma  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Tanıtımı](../../../../docs/framework/wcf/feature-details/routing-introduction.md)  
 [Sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [İleti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)
