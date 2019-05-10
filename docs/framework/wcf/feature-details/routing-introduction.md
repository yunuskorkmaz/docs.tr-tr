---
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 41545d0340ae222e427d1e6d428ed1e3f7b4fa76
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912486"
---
# <a name="routing-introduction"></a><span data-ttu-id="aec8c-102">Yönlendirme Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="aec8c-102">Routing Introduction</span></span>
<span data-ttu-id="aec8c-103">Yönlendirme hizmeti, yönlendirme iletilerinin ileti içeriğine göre yeteneğine sahip bir genel takılabilir SOAP aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="aec8c-104">Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelikli Yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolara olanak tanır ve yönlendirme karmaşık mantık oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aec8c-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="aec8c-105">Yönlendirme hizmeti, hata, işleme sağlar ve birincil hedef uç noktasına gönderilirken bir hata oluşması durumunda iletilerin gönderildiği listelerini yedekleme uç nokta ayarlamak de sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="aec8c-106">Bu konu için yönlendirme hizmeti için yeni yöneliktir ve temel yapılandırma ve yönlendirme hizmeti, barındırma kapsar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="aec8c-107">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aec8c-107">Configuration</span></span>  
 <span data-ttu-id="aec8c-108">Yönlendirme hizmeti, istemci uygulamalarından iletileri almak ve bir veya daha fazla hedef uç noktaları için iletileri yönlendirmek bir veya daha fazla hizmet uç noktayı kullanıma sokan bir WCF hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="aec8c-109">Hizmeti sağlayan bir <xref:System.ServiceModel.Routing.RoutingBehavior>, hizmet tarafından sunulan hizmet uç noktalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="aec8c-110">Bu davranış, hizmetin nasıl çalıştığı çeşitli yönlerini yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="aec8c-111">Bir yapılandırma dosyası kullanarak yapılandırma kolaylığı için parametreleri üzerinde belirtilen **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="aec8c-112">Kod tabanlı senaryolarda bu parametreleri bir parçası olarak belirtilecek bir <xref:System.ServiceModel.Routing.RoutingConfiguration> ardından geçirilebilir nesnesi bir **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="aec8c-113">Başlatma sırasında bu davranışı ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, istemci uç noktalarına iletilerin SOAP işleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="aec8c-114">Farklı bir gerektiren uç noktalarına ileti aktarmaya yönlendirme hizmeti böylece **MessageVersion** daha uç nokta üzerinden ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="aec8c-115">**RoutingBehavior** de bir hizmet uzantısı kaydeder <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için bir erişilebilirlik noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="aec8c-116">**RoutingConfiguration** sınıfı, yapılandırma ve yönlendirme hizmeti yapılandırmasını güncelleştirmek için tutarlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="aec8c-117">Yönlendirme hizmeti ayarlarını görür ve yapılandırmak için kullanılan parametreleri içeren **RoutingBehavior** hizmet yeniden başlatıldığında veya geçirilir **RoutingExtension** yönlendirme değiştirmek için Çalışma zamanında yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="aec8c-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="aec8c-118">İçerik tabanlı yönlendirme iletilerinin gerçekleştirmek için kullanılan yönlendirme mantığı birden çok gruplandırma tarafından tanımlanan <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri ile birlikte filtre tablolar (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneleri).</span><span class="sxs-lookup"><span data-stu-id="aec8c-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="aec8c-119">Gelen iletileri filtre tabloda ve her ileti filtreleri karşı değerlendirilir **MessageFilter** iletinin bir hedef uç noktasına iletilen eşleşir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="aec8c-120">İletileri yönlendirmek için kullanılan filtre tabloyu kullanarak belirtilen **RoutingBehavior** yapılandırma veya kod kullanarak **RoutingConfiguration** nesne.</span><span class="sxs-lookup"><span data-stu-id="aec8c-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="aec8c-121">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="aec8c-121">Defining Endpoints</span></span>  
 <span data-ttu-id="aec8c-122">Kullanacağınız yönlendirme mantığı tanımlayarak yapılandırmanızı başlaması gerektiğini görünebilir, ancak ilk adımınız yönlendirme iletileri olacaktır uç noktaları şeklini belirlemek için gerçekten olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="aec8c-123">Yönlendirme hizmeti almak ve göndermek için kullanılan kanalları şeklini tanımlayan sözleşme kullanır ve bu nedenle Giriş kanalı şeklini çıkış kanalının eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="aec8c-124">İstek-yanıt kanal şekli kullanan uç noktaları için yönlendirdiğinden, örneğin, ardından uyumlu bir sözleşme gelen uç noktalar gibi kullanmalısınız <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="aec8c-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="aec8c-125">Başka bir deyişle, hedef uç noktaları (örneğin, tek yönlü ve çift yönlü işlemleri karıştırma) birden çok kimlik doğrulaması desenleri ile sözleşmeler kullanırsanız, bu bildirimleri alabilen ve bunların tümüne iletileri yönlendirmek bir tek hizmet uç noktası oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="aec8c-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="aec8c-126">Hangi uç noktaları uyumlu şekilleri sahip ve hedef Uç noktalara yönlendirilmesi için iletileri almak için kullanılacak bir veya daha fazla hizmet uç noktaları tanımlamak belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aec8c-127">Belirtin (örneğin, tek yönlü ve çift yönlü işlemlerin bir karışımı) birden çok desenleri sözleşmeleri ile çalışırken, geçici bir çözüm çift yönlü sözleşme yönlendirme hizmeti gibi kullanmaktır <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="aec8c-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="aec8c-128">Ancak bu bağlama için tüm senaryoları mümkün olmayabilir çift yönlü iletişim özellikli olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="aec8c-129">Bu mümkün olduğu senaryolarda yazışmaya birden fazla uç nokta hesaba katacak şekilde veya uygulamayı değiştirmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="aec8c-130">Sözleşmeleri yönlendirme hakkında daha fazla bilgi için bkz: [sözleşmeleri yönlendirme](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="aec8c-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="aec8c-131">Hizmet uç noktası tanımlandıktan sonra kullanabileceğiniz **RoutingBehavior** belirli bir ilişkilendirilecek **RoutingConfiguration** uç nokta ile.</span><span class="sxs-lookup"><span data-stu-id="aec8c-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="aec8c-132">Yönlendirme hizmeti bir yapılandırma dosyası kullanarak yapılandırırken **RoutingBehavior** Bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığı içeren filtre tablo belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="aec8c-133">Yönlendirme hizmeti programlı bir şekilde yapılandırıyorsanız kullanarak filtreleme tablosu belirtebilirsiniz **RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="aec8c-134">Aşağıdaki örnek, programlı ve bir yapılandırma dosyası kullanarak yönlendirme hizmeti tarafından kullanılan hizmet ve istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 <span data-ttu-id="aec8c-135">Bu örnek bir adresi olan tek bir uç nokta kullanıma sunmak için yönlendirme hizmetini yapılandırır `http://localhost:8000/routingservice/router`, yönlendirilmesini iletileri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="aec8c-136">Hizmet uç noktası kullanır, iletileri istek-yanıt Uç noktalara yönlendirilir çünkü <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşme.</span><span class="sxs-lookup"><span data-stu-id="aec8c-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="aec8c-137">Bu yapılandırma aynı zamanda tek istemcisi bitiş noktasının tanımlar `http://localhost:8000/servicemodelsample/service` iletiler için yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="aec8c-138">"RoutingTable1" adlı (gösterilmemiştir) filtre tablo iletileri yönlendirmek için kullanılan yönlendirme mantığı içerir ve hizmet uç noktası ile ilişkili olup'ı kullanarak **RoutingBehavior** (için bir yapılandırma dosyası) veya  **RoutingConfiguration** (için program yapılandırması).</span><span class="sxs-lookup"><span data-stu-id="aec8c-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="aec8c-139">Yönlendirme mantığı</span><span class="sxs-lookup"><span data-stu-id="aec8c-139">Routing Logic</span></span>  
 <span data-ttu-id="aec8c-140">İletileri yönlendirmek için kullanılan yönlendirme mantığı tanımlamak için hangi gelen iletileri içinde bulunan verileri belirlemeniz gerekir bağlı benzersiz olarak eylem gerçekleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="aec8c-141">İleti içinde yer alan eylem değerini aynı SOAP eylemleri paylaşmak için yönlendirme tüm hedef uç noktaları değilse, iyi bir göstergesi gibi belirli hangi uç noktaya, ileti için yönlendirileceğini.</span><span class="sxs-lookup"><span data-stu-id="aec8c-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="aec8c-142">İletileri belirli bir uç nokta için benzersiz bir şekilde yönlendirmek gerekir, ileti yönlendirilir hedef uç nokta benzersiz olarak tanımlayan veri üzerine filtre.</span><span class="sxs-lookup"><span data-stu-id="aec8c-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="aec8c-143">Yönlendirme hizmeti birkaç sağlayan **MessageFilter** adresi, eylem, uç nokta adı veya hatta bir XPath sorgusu gibi ileti içindeki belirli değerleri inceleyin uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="aec8c-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="aec8c-144">Bu uygulamaların hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir oluşturabilirsiniz **MessageFilter** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="aec8c-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="aec8c-145">İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaları karşılaştırması hakkında daha fazla bilgi için bkz. [ileti filtreleri](message-filters.md) ve [filtre seçme](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="aec8c-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="aec8c-146">Birden çok ileti filtreleri birlikte her ilişkilendirmeniz filtre tablolarına düzenlenir **MessageFilter** hedef uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="aec8c-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="aec8c-147">İsteğe bağlı olarak, filtre tablosunda yönlendirme hizmeti için bir iletim hatası durumunda ileti göndermeye çalışır yedekleme uç noktalarının bir listesini belirtmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="aec8c-148">Varsayılan olarak tüm ileti filtreleri filtreleme tablosu içinde eşzamanlı olarak değerlendirilir; Ancak, belirtebileceğiniz bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> belirli bir sırada değerlendirilecek ileti filtreleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="aec8c-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="aec8c-149">En yüksek önceliğe sahip tüm girişleri ilk olarak değerlendirilir ve daha yüksek bir öncelik düzeyinde bir eşleşme bulunursa ileti filtreleri daha düşük önceliklerin değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="aec8c-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="aec8c-150">Filtre tabloları hakkında daha fazla bilgi için bkz. [ileti filtreleri](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="aec8c-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="aec8c-151">Aşağıdaki örneklerde <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, hangi değerlendirilen `true` tüm iletiler için.</span><span class="sxs-lookup"><span data-stu-id="aec8c-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="aec8c-152">Bu **MessageFilter** ilişkilendirir "routingTable1" filtre tablosuna ekleneceğinden **MessageFilter** "CalculatorService" adlı istemci uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="aec8c-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="aec8c-153">**RoutingBehavior** ardından bu tablo Hizmeti uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  <span data-ttu-id="aec8c-154">Varsayılan olarak, yönlendirme hizmeti, yalnızca ileti üstbilgileri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="aec8c-155">İleti gövdesi erişmek için filtreleri izin vermek için ayarlamanız gerekir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="aec8c-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="aec8c-156">**Çok noktaya yayın**</span><span class="sxs-lookup"><span data-stu-id="aec8c-156">**Multicast**</span></span>  
  
 <span data-ttu-id="aec8c-157">Birçok yönlendirme hizmeti yapılandırması için belirli tek bir uç nokta iletileri yönlendiren özel filtre mantığı kullanırken, belirli bir ileti birden çok hedef Uç noktalara yönlendirmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="aec8c-158">Çok noktaya yayın için birden fazla hedefe bir ileti, aşağıdaki koşulların doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="aec8c-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
- <span data-ttu-id="aec8c-159">Kanal şekli istek-yanıt olmamalıdır (ancak tek yönlü veya çift yönlü olabilir) çünkü isteğine yanıt olarak istemci uygulaması tarafından yalnızca bir yanıt aldı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
- <span data-ttu-id="aec8c-160">Birden çok filtre döndürmelidir `true` ileti değerlendirirken.</span><span class="sxs-lookup"><span data-stu-id="aec8c-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="aec8c-161">Bu koşullar karşılanıyorsa, ileti değerlendirmek için tüm filtre tüm uç noktalara yönlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="aec8c-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="aec8c-162">Aşağıdaki örnek, uç nokta adresini iletisi ise iki uç noktalara yönlendirilmek iletilerinde sonuçları bir yönlendirme yapılandırması tanımlar `http://localhost:8000/routingservice/router/rounding`.</span><span class="sxs-lookup"><span data-stu-id="aec8c-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a><span data-ttu-id="aec8c-163">SOAP işleme</span><span class="sxs-lookup"><span data-stu-id="aec8c-163">SOAP Processing</span></span>  
 <span data-ttu-id="aec8c-164">Benzer olmayan protokolleri arasında iletileri yönlendirme desteklemek için **RoutingBehavior** varsayılan ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletileri yönlendirilir tüm istemci uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="aec8c-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="aec8c-165">Bu davranışı otomatik olarak yeni bir oluşturur **MessageVersion** bir uyumlu oluşturma yanı sıra ileti uç noktaya yönlendirme önce **MessageVersion** için döndürmeden önce herhangi bir yanıt belge için istekte bulunan istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="aec8c-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="aec8c-166">Yeni bir oluşturmak için izlenen adımların **MessageVersion** için giden ileti şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="aec8c-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="aec8c-167">**İstek işleme**</span><span class="sxs-lookup"><span data-stu-id="aec8c-167">**Request processing**</span></span>  
  
- <span data-ttu-id="aec8c-168">Alma **MessageVersion** giden bağlama/kanal.</span><span class="sxs-lookup"><span data-stu-id="aec8c-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
- <span data-ttu-id="aec8c-169">Gövde Okuyucu için özgün iletisi görüntüleniyor.</span><span class="sxs-lookup"><span data-stu-id="aec8c-169">Get the body reader for the original message.</span></span>  
  
- <span data-ttu-id="aec8c-170">Aynı eylemi, gövde okuyucu ve yeni bir yeni bir ileti oluşturma **MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
- <span data-ttu-id="aec8c-171">Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, kopyalama ve yeni iletisi RelatesTo üst bilgi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="aec8c-172">Tüm ileti özelliklerini yeni iletinin kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-172">Copy all message properties to the new message.</span></span>  
  
- <span data-ttu-id="aec8c-173">Yanıtı işlerken kullanılacak özgün istek iletisi Store.</span><span class="sxs-lookup"><span data-stu-id="aec8c-173">Store the original request message to use when processing the response.</span></span>  
  
- <span data-ttu-id="aec8c-174">Yeni İstek iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="aec8c-175">**Yanıt işleme**</span><span class="sxs-lookup"><span data-stu-id="aec8c-175">**Response processing**</span></span>  
  
- <span data-ttu-id="aec8c-176">Alma **MessageVersion** özgün istek iletisi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-176">Get the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="aec8c-177">Gövde Okuyucu için alınan yanıt iletisi alın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-177">Get the body reader for the received response message.</span></span>  
  
- <span data-ttu-id="aec8c-178">Yeni bir yanıt iletisi gövdesi okuyucu aynı eylemi oluşturun ve **MessageVersion** özgün istek iletisi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="aec8c-179">Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, kopyalama ve yeni iletisi RelatesTo üst bilgi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="aec8c-180">Yeni ileti için ileti özelliklerinde kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-180">Copy the message properties to the new message.</span></span>  
  
- <span data-ttu-id="aec8c-181">Yeni bir yanıt iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="aec8c-182">Varsayılan olarak, **SoapProcessingBehavior** istemci uç noktaları tarafından otomatik olarak eklenir <xref:System.ServiceModel.Routing.RoutingBehavior> hizmet başladığında; ancak, SOAP işleme kullanarak tüm istemci uç noktaları için eklenen olup olmadığını kontrol edebilirsiniz <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aec8c-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="aec8c-183">Ayrıca doğrudan belirli bir uç davranışı eklemek ve da etkinleştirebilir veya SOAP işleme daha ayrıntılı bir denetim gerekiyorsa uç nokta düzeyinde bu davranışı devre dışı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aec8c-184">SOAP işleme özgün istek iletisi ait olandan farklı bir MessageVersion gerektiren bir uç nokta için devre dışı bırakılırsa, iletiyi göndermeden önce gerekli olan herhangi bir SOAP değişiklik gerçekleştirmek için özel bir mekanizma sağlamanız gerekir Hedef uç nokta.</span><span class="sxs-lookup"><span data-stu-id="aec8c-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="aec8c-185">Aşağıdaki örneklerde, **soapProcessingEnabled** önlemek için kullanılan özellik **SoapProcessingBehavior** için tüm istemci uç noktalarını otomatik olarak eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="aec8c-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="aec8c-186">Dinamik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aec8c-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="aec8c-187">Ek istemci uç noktalarını eklemek veya iletileri yönlendirmek için kullanılan filtreler değiştirmeniz gerekir, şu anda aracılığıyla iletileri alma uç noktaları için hizmet kesilmesini önlemek için dinamik olarak çalışma zamanında yapılandırmasını güncelleştirmek için bir yol olmalıdır. Yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="aec8c-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="aec8c-188">Her iki yöntem hiçbir ileti şu anda geçiş ve olası kaybı için kapalı kalma süresiyle için sunulmasını uygulamasını geri dönüşüme gerektiğinden bir yapılandırma dosyası veya ana bilgisayar uygulaması kodunu değiştirerek her zaman yeterli değildir hizmetin yeniden başlatılması bekliyor.</span><span class="sxs-lookup"><span data-stu-id="aec8c-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="aec8c-189">Yalnızca değiştirebileceğiniz **RoutingConfiguration** programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="aec8c-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="aec8c-190">Başlangıçta, bir yapılandırma dosyası kullanarak hizmet yapılandırabilirsiniz; ancak, yalnızca çalışma zamanında yapılandırmanın yeni bir oluşturarak değiştirebilirsiniz **RoutingConfigution** ve parametre olarak geçirerek <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yöntemi tarafından kullanıma sunulan <xref:System.ServiceModel.Routing.RoutingExtension> hizmet uzantısı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="aec8c-191">Şu anda yoldaki tüm iletileri çağrısından sonra alınan iletilerin çalışırken önceki yapılandırmayı kullanarak yönlendirilmesini devam **ApplyConfiguration** yeni yapılandırmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="aec8c-192">Aşağıdaki örnek, yönlendirme hizmeti örneği oluşturma ve daha sonra yapılandırmayı değiştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  <span data-ttu-id="aec8c-193">Bu şekilde yönlendirme hizmetini güncelleştirirken yalnızca yeni bir yapılandırma geçişi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="aec8c-194">Yalnızca seçilen öğelerin geçerli yapılandırmasını değiştirmek ya da yeni girişler geçerli yapılandırmasına eklemek mümkün değildir; oluşturur ve var olan bir yerini alan yeni bir yapılandırma geçişi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aec8c-195">Önceki yapılandırmayı kullanarak açılan tüm oturumları, önceki yapılandırmayı'ı kullanmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="aec8c-196">Yeni yapılandırma, yalnızca yeni oturumlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="aec8c-197">Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="aec8c-197">Error Handling</span></span>  
 <span data-ttu-id="aec8c-198">Varsa <xref:System.ServiceModel.CommunicationException> hata gerçekleştiğinde işleme bir ileti göndermeye çalışırken hatayla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="aec8c-199">Bu özel durumlar genellikle gibi tanımlı istemci uç noktası ile iletişim kurmaya çalışılırken bir sorunla karşılaşıldı gösterir bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="aec8c-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="aec8c-200">Hata işleme kodu ayrıca catch ve ne zaman göndermeyi yeniden deneme girişimi bir <xref:System.TimeoutException> gerçekleşir, türünden türetilmediğinden başka bir genel özel durum olduğu **CommunicationException**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="aec8c-201">Bir önceki özel durumlar oluştuğunda, yönlendirme hizmeti bir yedekleme uç noktalar listesine devreder.</span><span class="sxs-lookup"><span data-stu-id="aec8c-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="aec8c-202">Tüm yedekleme uç noktaları bir iletişim hatası ile başarısız veya bir uç nokta bir özel durum döndürürse, hedef hizmetinde bir hata gösteriyor, yönlendirme hizmeti bir hata istemci uygulamasına döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aec8c-203">Hata işleme işlevleri yakalar ve ileti göndermek çalışırken ve kanal kapatılmaya çalışılırken oluşan özel durumları işler.</span><span class="sxs-lookup"><span data-stu-id="aec8c-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="aec8c-204">Hata işleme kodu algılamak veya uygulama uç noktaları ile iletişim tarafından oluşturulan özel durumları işlemek üzere tasarlanmamıştır; bir <xref:System.ServiceModel.FaultException> tarafından oluşturulan bir hizmet yönlendirme hizmeti görünür bir **FaultMessage** ve istemciye geri akışı yapılan işlemler.</span><span class="sxs-lookup"><span data-stu-id="aec8c-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="aec8c-205">Yönlendirme hizmeti bir ileti geçiş çalıştığında bir hata oluşursa, alabilirsiniz bir <xref:System.ServiceModel.FaultException> istemci tarafında yerine <xref:System.ServiceModel.EndpointNotFoundException> normal olarak yönlendirme hizmeti olmaması durumunda elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="aec8c-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="aec8c-206">Yönlendirme hizmeti, böylece özel durumlarını maskeler ve iç içe geçmiş özel durumları incelemeniz sürece tam şeffaflık sağlamak.</span><span class="sxs-lookup"><span data-stu-id="aec8c-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="aec8c-207">Özel durum izleme</span><span class="sxs-lookup"><span data-stu-id="aec8c-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="aec8c-208">Yönlendirme hizmeti başarısız olursa listedeki bir uç nokta ileti gönderirken, sonuçta elde edilen özel durum verileri izler ve özel durum ayrıntıları adlı bir ileti özelliği ekler **özel durumları**.</span><span class="sxs-lookup"><span data-stu-id="aec8c-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="aec8c-209">Bu, özel durum verilerini korur ve bir ileti Inspector'ı aracılığıyla bir kullanıcının programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="aec8c-210">Özel durum verileri, her ileti bir ileti göndermeye çalışırken karşılaşılan özel durum ayrıntıları için uç nokta adına eşleyen bir sözlükte depolanır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="aec8c-211">Yedekleme uç noktaları</span><span class="sxs-lookup"><span data-stu-id="aec8c-211">Backup Endpoints</span></span>  
 <span data-ttu-id="aec8c-212">Her filtre giriş filtre tablo içindeki isteğe bağlı olarak bir iletim hatası durumunda birincil uç noktasına gönderilirken kullanılan yedekleme uç noktaları listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aec8c-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="aec8c-213">Böyle bir hata oluşursa, yönlendirme hizmeti, yedekleme uç nokta listesinde ilk girişe ileti gönderirken dener.</span><span class="sxs-lookup"><span data-stu-id="aec8c-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="aec8c-214">Bu gönderme girişimi de bir iletim hatası karşılaşırsa, sonraki uç nokta yedekleme listesinde denenir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="aec8c-215">Yönlendirme hizmeti, iletiyi başarıyla alınırsa, tüm uç noktaları bir iletim hatası döndürür veya bir olmayan iletim hatasının bir uç noktası tarafından döndürülen kadar listesindeki her bir uç nokta için ileti gönderilirken devam eder.</span><span class="sxs-lookup"><span data-stu-id="aec8c-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="aec8c-216">Aşağıdaki örnekler, yedekleme listesini kullanmak için yönlendirme hizmetini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a><span data-ttu-id="aec8c-217">Desteklenen hata desenleri</span><span class="sxs-lookup"><span data-stu-id="aec8c-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="aec8c-218">Aşağıdaki tabloda, yedekleme uç nokta listeleri, hata işleme için belirli desenleri ayrıntılarını açıklayan Notlar birlikte kullanımı ile uyumlu olan desenleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="aec8c-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="aec8c-219">Desen</span><span class="sxs-lookup"><span data-stu-id="aec8c-219">Pattern</span></span>|<span data-ttu-id="aec8c-220">Oturum</span><span class="sxs-lookup"><span data-stu-id="aec8c-220">Session</span></span>|<span data-ttu-id="aec8c-221">İşlem</span><span class="sxs-lookup"><span data-stu-id="aec8c-221">Transaction</span></span>|<span data-ttu-id="aec8c-222">Bağlamı alma</span><span class="sxs-lookup"><span data-stu-id="aec8c-222">Receive Context</span></span>|<span data-ttu-id="aec8c-223">Desteklenen yedekleme listesi</span><span class="sxs-lookup"><span data-stu-id="aec8c-223">Backup List Supported</span></span>|<span data-ttu-id="aec8c-224">Notlar</span><span class="sxs-lookup"><span data-stu-id="aec8c-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="aec8c-225">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-225">One-Way</span></span>||||<span data-ttu-id="aec8c-226">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-226">Yes</span></span>|<span data-ttu-id="aec8c-227">Bir yedekleme uç noktasında iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aec8c-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="aec8c-228">Bu ileti olup olmadığını çok noktaya yayın, yalnızca başarısız bir kanalda ileti, yedekleme hedefine taşınır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="aec8c-229">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-229">One-Way</span></span>||<span data-ttu-id="aec8c-230">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-230">✓</span></span>||<span data-ttu-id="aec8c-231">Hayır</span><span class="sxs-lookup"><span data-stu-id="aec8c-231">No</span></span>|<span data-ttu-id="aec8c-232">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="aec8c-233">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-233">One-Way</span></span>|||<span data-ttu-id="aec8c-234">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-234">✓</span></span>|<span data-ttu-id="aec8c-235">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-235">Yes</span></span>|<span data-ttu-id="aec8c-236">Bir yedekleme uç noktasında iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aec8c-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="aec8c-237">İleti sonra başarıyla alındı, tam tüm bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="aec8c-238">İleti tarafından herhangi bir uç noktası başarıyla alınmazsa alma bağlamı tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="aec8c-239">Bu ileti yükleniyor, çok noktaya yayın alma bağlamı ileti en az bir uç noktası tarafından (birincil veya yedek) başarıyla alınırsa yalnızca tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="aec8c-240">Uç noktaları çok noktaya yayın yollardan birinde hiçbiri başarılı bir şekilde iletisi alırsanız, alma bağlamı tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="aec8c-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="aec8c-241">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-241">One-Way</span></span>||<span data-ttu-id="aec8c-242">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-242">✓</span></span>|<span data-ttu-id="aec8c-243">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-243">✓</span></span>|<span data-ttu-id="aec8c-244">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-244">Yes</span></span>|<span data-ttu-id="aec8c-245">Önceki işlem durdurma, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="aec8c-246">Bir hatayla karşılaştı iletileri yedekleme hedefine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="aec8c-247">Bir işlem oluşturulduktan sonra tüm iletimler başarısız, alma bağlamı tamamlayın ve hareketi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="aec8c-248">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-248">One-Way</span></span>|<span data-ttu-id="aec8c-249">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-249">✓</span></span>|||<span data-ttu-id="aec8c-250">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-250">Yes</span></span>|<span data-ttu-id="aec8c-251">Bir yedekleme uç noktasında iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aec8c-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="aec8c-252">Bir çok noktaya yayın senaryosunda, yedekleme hedefi için yalnızca iletileri bir oturumda bir hatayla karşılaştı veya başarısız oturumunu kapatmak bir oturumda gönderilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="aec8c-253">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-253">One-Way</span></span>|<span data-ttu-id="aec8c-254">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-254">✓</span></span>|<span data-ttu-id="aec8c-255">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-255">✓</span></span>||<span data-ttu-id="aec8c-256">Hayır</span><span class="sxs-lookup"><span data-stu-id="aec8c-256">No</span></span>|<span data-ttu-id="aec8c-257">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="aec8c-258">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-258">One-Way</span></span>|<span data-ttu-id="aec8c-259">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-259">✓</span></span>||<span data-ttu-id="aec8c-260">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-260">✓</span></span>|<span data-ttu-id="aec8c-261">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-261">Yes</span></span>|<span data-ttu-id="aec8c-262">Bir yedekleme uç noktasında iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aec8c-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="aec8c-263">Tüm hata tamamlandı iletisi sonra oturumu başka iletilerin gösterir ve yönlendirme hizmeti başarıyla tüm giden oturumu kanallarınızı kapatır, tüm alma bağlamları tamamlanır ve gelen oturum kanalı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="aec8c-264">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-264">One-Way</span></span>|<span data-ttu-id="aec8c-265">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-265">✓</span></span>|<span data-ttu-id="aec8c-266">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-266">✓</span></span>|<span data-ttu-id="aec8c-267">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-267">✓</span></span>|<span data-ttu-id="aec8c-268">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-268">Yes</span></span>|<span data-ttu-id="aec8c-269">Geçerli işlem iptal edip yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aec8c-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="aec8c-270">Tüm önceki iletileri oturumunda yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="aec8c-271">Bir işlem, tüm ileti başarıyla gönderildi oluşturulduktan sonra daha fazla ileti, tüm giden oturum kanalları kapalı olduğundan, alma oturumu gösterir bağlamları tüm olan işlem tamamlanır, gelen oturum kanalı Kapalı, ve işlem taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="aec8c-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="aec8c-272">Çok noktaya yayın aynı hedefe önce herhangi bir hata vardı iletileri gönderilir ve hatayla iletileri oturumları ne zaman gönderildiğini yedekleme hedefi için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="aec8c-273">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-273">Two-Way</span></span>||||<span data-ttu-id="aec8c-274">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-274">Yes</span></span>|<span data-ttu-id="aec8c-275">Yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-275">Send to a backup destination.</span></span>  <span data-ttu-id="aec8c-276">Bir kanal bir yanıt iletisi döndürür. sonra özgün istemci yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="aec8c-277">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-277">Two-Way</span></span>|<span data-ttu-id="aec8c-278">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-278">✓</span></span>|||<span data-ttu-id="aec8c-279">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-279">Yes</span></span>|<span data-ttu-id="aec8c-280">Tüm iletileri kanalda yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="aec8c-281">Bir kanal bir yanıt iletisi döndürür. sonra özgün istemci yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="aec8c-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="aec8c-282">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-282">Two-Way</span></span>||<span data-ttu-id="aec8c-283">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-283">✓</span></span>||<span data-ttu-id="aec8c-284">Hayır</span><span class="sxs-lookup"><span data-stu-id="aec8c-284">No</span></span>|<span data-ttu-id="aec8c-285">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="aec8c-286">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-286">Two-Way</span></span>|<span data-ttu-id="aec8c-287">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-287">✓</span></span>|<span data-ttu-id="aec8c-288">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-288">✓</span></span>||<span data-ttu-id="aec8c-289">Hayır</span><span class="sxs-lookup"><span data-stu-id="aec8c-289">No</span></span>|<span data-ttu-id="aec8c-290">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="aec8c-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="aec8c-291">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-291">Duplex</span></span>||||<span data-ttu-id="aec8c-292">Hayır</span><span class="sxs-lookup"><span data-stu-id="aec8c-292">No</span></span>|<span data-ttu-id="aec8c-293">Çift yönlü iletişim olmayan oturumu şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="aec8c-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="aec8c-294">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="aec8c-294">Duplex</span></span>|<span data-ttu-id="aec8c-295">✓</span><span class="sxs-lookup"><span data-stu-id="aec8c-295">✓</span></span>|||<span data-ttu-id="aec8c-296">Evet</span><span class="sxs-lookup"><span data-stu-id="aec8c-296">Yes</span></span>|<span data-ttu-id="aec8c-297">Yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="aec8c-298">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aec8c-298">Hosting</span></span>  
 <span data-ttu-id="aec8c-299">Yönlendirme hizmeti bir WCF hizmeti olarak uygulandığından, bir uygulamadaki şirket içinde barındırılan veya barındırılan IIS ya da WAS tarafından.</span><span class="sxs-lookup"><span data-stu-id="aec8c-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="aec8c-300">Yönlendirme hizmeti, IIS, WAS veya bir Windows hizmeti uygulaması otomatik olarak başlamasını avantajlarından yararlanın ve yaşam döngüsü yönetim özellikleri bu barındırma ortamları kullanılabilir barındırılan önerilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="aec8c-301">Aşağıdaki örnek, bir uygulamada yönlendirme hizmeti barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="aec8c-302">Yönlendirme hizmeti IIS ya da WAS içinde barındırmak için bir hizmet dosyası (.svc) oluşturun veya hizmetin yapılandırma temelli etkinleştirme kullanın gerekir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="aec8c-303">Hizmet dosyasını kullanırken belirtmelisiniz <xref:System.ServiceModel.Routing.RoutingService> hizmet parametresini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="aec8c-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="aec8c-304">Aşağıdaki örnek, IIS veya WAS ile yönlendirme hizmeti barındırmak için kullanılan bir örnek hizmet dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="aec8c-305">Yönlendirme hizmeti ile kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="aec8c-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="aec8c-306">WCF yönlendirme hizmeti ile kimliğe bürünme hem ileti gönderme ve alma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="aec8c-307">Tüm kimliğe bürünme normal Windows kısıtlamaları uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="aec8c-308">Kimliğe bürünme kendi hizmet yazarken kullanmak için hizmet veya hesap izinlerini ayarlamak gerekli olursa, kimliğe bürünme yönlendirme hizmeti ile kullanmak için bu aynı adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="aec8c-309">Daha fazla bilgi için [temsilcilik ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="aec8c-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="aec8c-310">Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET kimliğe bürünme modunda ASP.NET uyumluluk kullanımı ya da kimliğe bürünme izin verecek şekilde yapılandırılmış bir Windows kimlik bilgilerinin kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="aec8c-311">ASP.NET uyumluluğu modu hakkında daha fazla bilgi için bkz. [WCF hizmetleri ve ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="aec8c-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="aec8c-312">WCF yönlendirme hizmeti, temel kimlik doğrulaması ile kimliğe bürünme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aec8c-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="aec8c-313">ASP.NET kimliğe bürünme yönlendirme hizmeti ile kullanmak için hizmet barındırma ortamını ASP.NET uyumluluk modu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="aec8c-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="aec8c-314">Yönlendirme hizmeti, zaten ASP.NET uyumluluk modunun ve kimliğe bürünme otomatik olarak etkinleştirilecek izin verecek şekilde işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="aec8c-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="aec8c-315">Kimliğe bürünme ASP.NET tümleştirme yönlendirme hizmeti ile yalnızca desteklenen kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="aec8c-316">Windows kimlik bilgisi kimliğe bürünme yönlendirme hizmeti ile kullanmak için kimlik bilgilerini hem service'ı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aec8c-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="aec8c-317">İstemci kimlik bilgileri nesnesi (<xref:System.ServiceModel.Security.WindowsClientCredential>, gelen erişilebilir operasyonlar <xref:System.ServiceModel.ChannelFactory>) tanımlayan bir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> kimliğe bürünme izin vermek için ayarlanmalıdır özelliği.</span><span class="sxs-lookup"><span data-stu-id="aec8c-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="aec8c-318">Son olarak, hizmette yapılandırmanız gereken <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ayarlamak için davranış `ImpersonateCallerForAllOperations` için `true`.</span><span class="sxs-lookup"><span data-stu-id="aec8c-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="aec8c-319">Yönlendirme hizmeti ile kişileştirme etkinleştirildi iletilerini yönlendirmede istemcileri oluşturma karar vermek için bu bayrağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="aec8c-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec8c-320">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec8c-320">See also</span></span>

- [<span data-ttu-id="aec8c-321">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="aec8c-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="aec8c-322">Anlaşmaları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="aec8c-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="aec8c-323">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="aec8c-323">Choosing a Filter</span></span>](choosing-a-filter.md)
