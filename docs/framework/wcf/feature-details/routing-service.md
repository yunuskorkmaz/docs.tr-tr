---
title: Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 833c824e17d70a982a2f7bb13fe388b9b2b0dec1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590455"
---
# <a name="routing-service"></a>Yönlendirme Hizmeti

Yönlendirme hizmeti, ileti yönlendiricisi görevi gören genel bir SOAP aracısıyla bulunur. Yönlendirme hizmeti 'nin temel işlevselliği iletileri ileti içeriğine göre yönlendirmenize olanak tanır. Bu, iletinin üstbilgisinde veya ileti gövdesinde bulunan bir değere bağlı olarak bir istemci uç noktasına iletime olanağı sağlar.

, <xref:System.ServiceModel.Routing.RoutingService> Ad alanında Windows Communication Foundation (WCF) hizmeti olarak uygulanır <xref:System.ServiceModel.Routing> . Yönlendirme hizmeti, ileti alan bir veya daha fazla hizmet uç noktası gösterir ve ileti içeriğine göre her iletiyi bir veya daha fazla istemci uç noktasına yönlendirir. Hizmet aşağıdaki özellikleri sağlar:

- İçerik tabanlı yönlendirme

  - Hizmet toplama

  - Hizmet sürümü oluşturma

  - Öncelikli yönlendirme

  - Dinamik yapılandırma

- Protokol köprüleme

- SOAP işleme

- Gelişmiş hata işleme

- Yedekleme uç noktaları

Bu amaçlardan birini veya daha fazlasını gerçekleştiren bir ara hizmet oluşturmak mümkün olsa da, genellikle bu tür bir uygulama belirli bir senaryoya veya çözüme bağlanır ve yeni uygulamalara kolayca uygulanmaz.

Yönlendirme hizmeti, WCF hizmeti ve kanal modelleriyle uyumlu genel, dinamik olarak yapılandırılabilir ve takılabilir bir SOAP aracı sağlar ve SOAP tabanlı iletilerin içerik tabanlı yönlendirilmesini gerçekleştirmenize olanak tanır.

> [!NOTE]
> Yönlendirme hizmeti şu anda WCF REST hizmetlerinin yönlendirilmesini desteklememektedir.  REST çağrılarını yönlendirmek için <xref:System.Web.Routing> veya [uygulama isteği yönlendirme](https://go.microsoft.com/fwlink/?LinkId=164589)kullanmayı düşünün.

## <a name="content-based-routing"></a>İçerik tabanlı yönlendirme

İçerik tabanlı yönlendirme, ileti içinde bulunan bir veya daha fazla değere göre bir iletiyi yönlendirmenize olanak tanır. Yönlendirme hizmeti her iletiyi inceler ve ileti içeriğine ve oluşturduğunuz yönlendirme mantığına göre hedef uç noktaya yönlendirir. İçerik tabanlı yönlendirme, hizmet toplama, hizmet sürümü oluşturma ve öncelik yönlendirmenin temelini sağlar.

İçerik tabanlı yönlendirme uygulamak için yönlendirme hizmeti, <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirilecek iletiler içindeki belirli değerleri eşleştirmek için kullanılan uygulamaları kullanır. Bir **MessageFilter** bir iletiyle eşleşiyorsa Ileti, **MessageFilter**ile ilişkili hedef uç noktaya yönlendirilir.  İleti filtreleri <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection> karmaşık yönlendirme mantığı oluşturmak için filtre tablolarında () birlikte gruplandırılır. Örneğin, bir filtre tablosu, iletilerin yalnızca beş hedef uç noktasından yalnızca birine yönlendirilmesine neden olan beş karşılıklı dışlamalı ileti filtresi içerebilir.

Yönlendirme hizmeti, içerik tabanlı yönlendirme gerçekleştirmek için kullanılan mantığı yapılandırmanıza ve aynı zamanda yönlendirme mantığını çalışma zamanında dinamik olarak güncelleyebilmesini sağlar.

İleti filtrelerini filtre tablolarına gruplandırarak, yönlendirme mantığı, şöyle bir şekilde birden çok yönlendirme senaryosunu işleyebilmeniz için oluşturulabilir:

- Hizmet toplama

- Hizmet sürümü oluşturma

- Öncelikli yönlendirme

- Dinamik yapılandırma

İleti filtreleri ve filtre tabloları hakkında daha fazla bilgi için bkz. [yönlendirme tanıtımı](routing-introduction.md) ve [ileti filtreleri](message-filters.md).

### <a name="service-aggregation"></a>Hizmet toplama

İçerik tabanlı yönlendirmeyi kullanarak, dış istemci uygulamalarından iletiler alan bir uç noktayı kullanıma sunabilir ve sonra ileti içindeki bir değere göre her iletiyi uygun iç uç noktaya yönlendirir. Bu, çeşitli arka uç uygulamaları için belirli bir uç nokta sunmak ve ayrıca, uygulamanızı çeşitli hizmetlere düzenleme sırasında bir uygulama uç noktası sunmak için yararlıdır.

### <a name="service-versioning"></a>Hizmet Sürümü Oluşturma

Çözümünüzün yeni bir sürümüne geçiş yaparken, mevcut müşterileri karşılamak için eski sürümü paralel olarak korumanız gerekebilir. Genellikle bu, yeni sürüme bağlanan istemcilerin Çözümle iletişim kurarken farklı bir adres kullanması gerekir. Yönlendirme hizmeti, iletileri iletide bulunan sürüme özgü bilgilere göre uygun çözüme yönlendirerek, her iki çözümün her iki sürümüne de hizmet veren bir hizmet uç noktasını kullanıma sunmasına olanak tanır. Bu tür bir uygulamayla ilgili bir örnek için bkz. [nasıl yapılır: hizmet sürümü oluşturma](how-to-service-versioning.md).

### <a name="priority-routing"></a>Öncelik yönlendirme

Birden çok istemci için bir hizmet sağlarken, bu iş ortaklarının tüm verilerinin diğer istemcilerden ayrı olarak işlenmesini gerektiren bazı iş ortakları ile bir hizmet düzeyi anlaşması (SLA) olabilir. İletide yer alan müşteriye özgü bilgileri gösteren bir filtre kullanarak, belirli iş ortaklarından alınan iletileri, SLA gereksinimlerini karşılayacak şekilde oluşturulmuş bir uç noktaya kolayca yönlendirebilirsiniz.

## <a name="dynamic-configuration"></a>Dinamik yapılandırma

İletilerin hiçbir hizmet kesintisi olmadan işlenmesi gereken görev açısından kritik sistemleri desteklemek için, çalışma zamanında sistem içindeki bileşenlerin yapılandırmasını değiştirebilmelisiniz. Bu gereksinimi desteklemek için, yönlendirme hizmeti, <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.Routing.RoutingExtension> çalışma zamanında yönlendirme hizmeti yapılandırmasının dinamik güncelleştirilmesini sağlayan bir uygulama sağlar.

Yönlendirme hizmetinin dinamik yapılandırması hakkında daha fazla bilgi için bkz. [yönlendirme tanıtımı](routing-introduction.md).

## <a name="protocol-bridging"></a>Protokol köprüleme

Ara senaryolarındaki güçlüklerden biri iç uç noktaların, iletilerin alındığı uç noktadan farklı aktarım veya SOAP sürümü gereksinimlerine sahip olabileceği bir noktadır. Bu senaryoyu desteklemek için, yönlendirme hizmeti, SOAP iletisini hedef uç noktaları için gereken şekilde işleme dahil olmak üzere protokolleri köprü oluşturabilir <xref:System.ServiceModel.Channels.MessageVersion> . Bu şekilde, dahili iletişim için bir protokol kullanılabilir, diğeri dış iletişim için kullanılabilir.

Farklı aktarımlara sahip uç noktalar arasında ileti yönlendirmeyi desteklemek için, yönlendirme hizmeti hizmetin benzer olmayan protokolleri köprülemek için sistem tarafından sağlanmış bağlamaları kullanır. Bu, yönlendirme hizmeti tarafından açığa çıkarılan hizmet uç noktası, iletilerin yönlendirildiği istemci uç noktalarından farklı bir protokol kullandığında otomatik olarak gerçekleşir.

## <a name="soap-processing"></a>SOAP Işleme

Ortak bir yönlendirme gereksinimi, iletileri farklı SOAP gereksinimleriyle uç noktalar arasında yönlendirmenize olanak tanır. Bu gereksinimi desteklemek için yönlendirme hizmeti, <xref:System.ServiceModel.Routing.SoapProcessingBehavior> ileti kendisine yönlendirilmeden önce hedef uç noktasının gereksinimlerini karşılayan yeni bir **MessageVersion** otomatik olarak oluşturduğunu bir sağlar. Bu davranış ayrıca, yanıtın **MessageVersion** 'ın özgün istekten eşleştiğinden emin olmak için, istek yapan istemci uygulamasına döndürmeden önce herhangi bir yanıt iletisi için yeni bir **MessageVersion** oluşturur.

SOAP işleme hakkında daha fazla bilgi için bkz. [yönlendirme tanıtımı](routing-introduction.md).

## <a name="error-handling"></a>Hata İşleme

Ağ iletişimlerini kullanan dağıtılmış hizmetlerden oluşan bir sistemde, sisteminizdeki iletişimin geçici ağ hatalarıyla dayanıklı olduğundan emin olmak önemlidir.  Yönlendirme hizmeti, başka bir hizmet kesintisine neden olabilecek birçok iletişim hatası senaryosunu işleyemenizi sağlayan hata işleme uygular.

Yönlendirme hizmeti bir ileti gönderilmeye çalışırken bir hata ile karşılaştığında <xref:System.ServiceModel.CommunicationException> , hata işleme gerçekleşmeyecektir.  Bu özel durumlar genellikle, veya gibi tanımlı istemci uç noktasıyla iletişim kurmaya çalışırken bir sorunla karşılaşıldığını gösterir <xref:System.ServiceModel.EndpointNotFoundException> <xref:System.ServiceModel.ServerTooBusyException> <xref:System.ServiceModel.CommunicationObjectFaultedException> .  Hata işleme kodu Ayrıca, **CommunicationException**'dan türetilmeyen başka bir ortak özel durum olan bir **TimeoutException** gerçekleştiğinde göndermeyi yeniden denemeye çalışır.

Hata işleme hakkında daha fazla bilgi için bkz. [yönlendirme tanıtımı](routing-introduction.md).

## <a name="backup-endpoints"></a>Yedekleme uç noktaları

Filtre tablosundaki her bir filtre tanımıyla ilişkili hedef istemci uç noktalarına ek olarak, bir iletim hatası durumunda iletinin yönlendirileceği yedekleme uç noktalarının bir listesini de oluşturabilirsiniz. Bir hata oluşursa ve filtre girişi için bir yedekleme listesi tanımlanmışsa, yönlendirme hizmeti iletiyi listede tanımlanan ilk uç noktaya göndermeye çalışır. Bu iletim girişimi başarısız olursa, hizmet sonraki uç noktayı dener ve iletim girişimi başarılı olana kadar bu işleme devam eder, iletime yönelik olmayan bir hata döndürür veya yedekleme listesindeki tüm uç noktalar bir iletim hatası döndürmeyecektir.

Yedekleme uç noktaları hakkında daha fazla bilgi için bkz. [yönlendirme tanıtımı](routing-introduction.md) ve [ileti filtreleri](message-filters.md).

## <a name="streaming"></a>Akış

Akışı desteklemek için bağlamayı ayarlarsanız yönlendirme hizmeti iletileri başarıyla akışa alabilir.  Ancak, iletilerin arabelleğe alınmaları gerekebilecek bazı koşullar vardır:

- Çok noktaya yayın (ek ileti kopyaları oluşturmak için arabellek)

- Yük devretme (iletinin bir yedeklemeye gönderilmesi gerektiğinde arabellek)

- System. ServiceModel. Routing. RoutingConfiguration. RouteOnHeadersOnly false 'dur (filtrelerin gövdeyi inceleyebilmesi için bir MessageBuffer ile MessageFilterTable sunma arabelleği)

- Dinamik yapılandırma

## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Tanıtımı](routing-introduction.md)
- [Anlaşmaları Yönlendirme](routing-contracts.md)
- [İleti Filtreleri](message-filters.md)
