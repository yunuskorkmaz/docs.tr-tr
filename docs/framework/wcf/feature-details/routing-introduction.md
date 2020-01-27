---
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746471"
---
# <a name="routing-introduction"></a><span data-ttu-id="3f6c1-102">Yönlendirme Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="3f6c1-102">Routing Introduction</span></span>

<span data-ttu-id="3f6c1-103">Yönlendirme hizmeti ileti içeriğine göre iletileri yönlendirme yeteneğine sahip genel bir takılabilir SOAP aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="3f6c1-104">Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelik yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolar uygulamanıza olanak tanıyan karmaşık yönlendirme mantığı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="3f6c1-105">Yönlendirme hizmeti Ayrıca, birincil hedef uç noktasına gönderilirken bir hata oluşursa gönderilecek olan yedekleme uç noktaları listesini ayarlamanıza olanak tanıyan hata işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="3f6c1-106">Bu konu, yönlendirme hizmeti için yeni olanlar için tasarlanmıştır ve temel yapılandırmayı ve yönlendirme hizmetinin barındırılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="3f6c1-107">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f6c1-107">Configuration</span></span>

<span data-ttu-id="3f6c1-108">Yönlendirme hizmeti, istemci uygulamalarından ileti alan ve iletileri bir veya daha fazla hedef uç noktaya yönlendiren bir veya daha fazla hizmet uç noktası sunan bir WCF hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="3f6c1-109">Hizmet, hizmet tarafından açığa çıkarılan hizmet uç noktalarına uygulanan bir <xref:System.ServiceModel.Routing.RoutingBehavior>sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="3f6c1-110">Bu davranış, hizmetin nasıl çalıştığı hakkında çeşitli yönleri yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="3f6c1-111">Yapılandırma dosyası kullanılırken yapılandırma kolaylığı için, parametreler **RoutingBehavior**üzerinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="3f6c1-112">Kod tabanlı senaryolarda, bu parametreler bir <xref:System.ServiceModel.Routing.RoutingConfiguration> nesnesinin parçası olarak belirtilir ve bu daha sonra bir **RoutingBehavior**'a geçirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="3f6c1-113">Bu davranış başlatıldığında, istemci uç noktalarına iletilerin SOAP işlemesini gerçekleştirmek için kullanılan <xref:System.ServiceModel.Routing.SoapProcessingBehavior>ekler.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="3f6c1-114">Bu, yönlendirme hizmetinin ileti alındığı uç noktadan farklı bir **MessageVersion** gerektiren uç noktalara ileti aktarmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="3f6c1-115">**RoutingBehavior** Ayrıca, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için bir erişilebilirlik noktası sağlayan <xref:System.ServiceModel.Routing.RoutingExtension>bir hizmet uzantısı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="3f6c1-116">**RoutingConfiguration** sınıfı, yönlendirme hizmeti yapılandırmasını yapılandırmak ve güncelleştirmek için tutarlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="3f6c1-117">Yönlendirme hizmeti için ayarlar olarak davranan ve hizmet başlatıldığında **RoutingBehavior** 'ı yapılandırmak için kullanılan ve çalışma zamanında yönlendirme yapılandırmasını değiştirmek Için **RoutingExtension** 'a geçirilen parametreleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="3f6c1-118">İletilerin içerik tabanlı yönlendirilmesini gerçekleştirmek için kullanılan yönlendirme mantığı, birden çok <xref:System.ServiceModel.Dispatcher.MessageFilter> nesnesini, filtre tabloları (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneleri) halinde gruplandırarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="3f6c1-119">Gelen iletiler, filtre tablosunda bulunan ileti filtrelerine ve bir hedef uç noktaya iletilen iletiyle eşleşen her **MessageFilter** için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="3f6c1-120">İletileri yönlendirmek için kullanılması gereken filtre tablosu, yapılandırma veya **RoutingConfiguration** nesnesi kullanılarak kod aracılığıyla yönlendirme **davranışı** kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="3f6c1-121">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="3f6c1-121">Defining Endpoints</span></span>

<span data-ttu-id="3f6c1-122">Kullanacağınız yönlendirme mantığını tanımlayarak yapılandırmanızı başlatmanız gerektiği gibi görünse de, ilk adımınız ileti yönlendirdiğiniz uç noktaların şeklini belirlemektir, gerçekten yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="3f6c1-123">Yönlendirme hizmeti, iletileri almak ve göndermek için kullanılan kanalların şeklini tanımlayan sözleşmeleri kullanır ve bu nedenle, giriş kanalının şekli çıkış kanalının ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="3f6c1-124">Örneğin, istek-yanıt kanalı şeklini kullanan uç noktalara yönlendirmeniz durumunda, <xref:System.ServiceModel.Routing.IRequestReplyRouter>gibi gelen uç noktalarında uyumlu bir sözleşme kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="3f6c1-125">Yani, hedef uç noktalarınız birden çok iletişim deseniyle (tek yönlü ve iki yönlü işlemleri karıştırma gibi) sözleşmeler kullanıyorsa, bunlara ileti alabilen ve bunlara yönlendirebileceği tek bir hizmet uç noktası oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="3f6c1-126">Hangi uç noktaların uyumlu şekillere sahip olduğunu ve hedef uç noktalara yönlendirilmek üzere ileti almak için kullanılacak bir veya daha fazla hizmet uç noktası tanımlanacağını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="3f6c1-127">Birden çok iletişim deseni (tek yönlü ve iki yönlü işlemlerin karışımı gibi) belirten sözleşmelerle çalışırken, bir geçici çözüm, yönlendirme hizmetinde <xref:System.ServiceModel.Routing.IDuplexSessionRouter>gibi bir çift yönlü sözleşme kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="3f6c1-128">Ancak bu, bağlamanın çift yönlü iletişim özelliği olması gerektiği anlamına gelir. Bu, tüm senaryolarda mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="3f6c1-129">Bunun mümkün olmadığı senaryolarda, iletişimin birden çok uç noktaya düzenleme veya uygulamanın değiştirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="3f6c1-130">Yönlendirme sözleşmeleri hakkında daha fazla bilgi için bkz. [yönlendirme sözleşmeleri](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="3f6c1-131">Hizmet uç noktası tanımlandıktan sonra, belirli bir **RoutingConfiguration** 'ı uç noktayla Ilişkilendirmek Için **RoutingBehavior** 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="3f6c1-132">Yönlendirme hizmetini bir yapılandırma dosyası kullanarak yapılandırırken, bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığını içeren filtre tablosunu belirtmek için **RoutingBehavior** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="3f6c1-133">Yönlendirme hizmetini programlı olarak yapılandırıyorsanız, **RoutingConfiguration**kullanarak filtre tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="3f6c1-134">Aşağıdaki örnek, yönlendirme hizmeti tarafından hem programlı olarak hem de bir yapılandırma dosyası kullanılarak kullanılan hizmet ve istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

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

<span data-ttu-id="3f6c1-135">Bu örnek, yönlendirme hizmetini, yönlendirileceği iletileri almak için kullanılan `http://localhost:8000/routingservice/router`adresiyle tek bir uç nokta kullanıma sunulacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="3f6c1-136">İletiler istek-yanıt uç noktalarına yönlendirildiğinden, hizmet uç noktası <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="3f6c1-137">Bu yapılandırma ayrıca iletilerin yönlendirildiği `http://localhost:8000/servicemodelsample/service` tek bir istemci uç noktasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="3f6c1-138">"RoutingTable1" adlı Filtre tablosu (gösterilmez), iletileri yönlendirmek için kullanılan yönlendirme mantığını içerir ve **RoutingBehavior** (bir yapılandırma dosyası için) veya **RoutingConfiguration** (programlı yapılandırma için) kullanılarak hizmet uç noktasıyla ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="3f6c1-139">Yönlendirme mantığı</span><span class="sxs-lookup"><span data-stu-id="3f6c1-139">Routing Logic</span></span>

<span data-ttu-id="3f6c1-140">İletileri yönlendirmek için kullanılan yönlendirme mantığını tanımlamak için, gelen iletilerde bulunan verilerin üzerinde benzersiz olarak işlem yapabileceğini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="3f6c1-141">Örneğin, tüm hedef uç noktaları aynı SOAP eylemlerini paylaşmak üzere yönlendirdiğiniz takdirde, ileti içinde yer alan eylemin değeri iletinin hangi belirli uç noktada yönlendirildiğini belirten iyi bir göstergedir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="3f6c1-142">İletileri belirli bir uç noktaya benzersiz bir şekilde yönlendirmelisiniz, iletinin yönlendirildiği hedef uç noktayı benzersiz şekilde tanımlayan verileri filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="3f6c1-143">Yönlendirme hizmeti, ileti içindeki adres, eylem, uç nokta adı ve hatta bir XPath sorgusu gibi belirli değerleri denetleyen çeşitli **MessageFilter** uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="3f6c1-144">Bu uygulamalardan hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir **MessageFilter** uygulaması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="3f6c1-145">İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaların karşılaştırması hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md) ve [bir filtre seçme](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="3f6c1-146">Birden çok ileti filtresi, her **MessageFilter** öğesini bir hedef uç noktasıyla ilişkilendiren filtre tablolarında birlikte düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="3f6c1-147">İsteğe bağlı olarak, bir aktarım hatası durumunda yönlendirme hizmetinin iletiyi göndermek için deneyeceği yedek uç noktaların listesini belirtmek için filtre tablosu da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="3f6c1-148">Varsayılan olarak, bir filtre tablosu içindeki tüm ileti filtreleri aynı anda değerlendirilir; Ancak, ileti filtrelerinin belirli bir sırada değerlendirilmesine neden olan bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="3f6c1-149">En yüksek önceliğe sahip tüm girişler önce değerlendirilir ve daha yüksek bir öncelik düzeyinde eşleşme bulunursa düşük önceliklerdeki ileti filtreleri değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="3f6c1-150">Filtre tabloları hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="3f6c1-151">Aşağıdaki örneklerde, tüm iletiler için `true` değerlendirilen <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="3f6c1-152">Bu **MessageFilter** , "routingTable1" filtre tablosuna eklenir ve bu, **MessageFilter** öğesini "hesaplatorservice" adlı istemci uç noktasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="3f6c1-153">**RoutingBehavior** daha sonra bu tablonun hizmet uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

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
> <span data-ttu-id="3f6c1-154">Varsayılan olarak, yönlendirme hizmeti yalnızca iletinin üstbilgilerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="3f6c1-155">Filtrelerin ileti gövdesine erişmesine izin vermek için <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> `false`ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="3f6c1-156">**Noktalı**</span><span class="sxs-lookup"><span data-stu-id="3f6c1-156">**Multicast**</span></span>

<span data-ttu-id="3f6c1-157">Birçok yönlendirme hizmeti yapılandırması iletileri yalnızca belirli bir uç noktaya yönlendiren özel durum filtre mantığı kullanır, ancak belirli bir iletiyi birden çok hedef uç noktaya yönlendirmenize gerek vardır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="3f6c1-158">Bir iletinin birden çok hedefe çok noktaya yayını olması için aşağıdaki koşulların doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="3f6c1-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="3f6c1-159">İstek yanıtındaki istemci uygulaması tarafından yalnızca bir yanıt alınabileceğinden, kanal şeklinin istek Yanıtla (ancak tek yönlü veya çift yönlü olabilir) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="3f6c1-160">İleti değerlendirilirken birden çok filtrenin `true` döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-160">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="3f6c1-161">Bu koşullar karşılanıyorsa, ileti `true`sonucunu değerlendiren tüm filtrelerin tüm uç noktalarına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="3f6c1-162">Aşağıdaki örnek, iletideki bitiş noktası adresi `http://localhost:8000/routingservice/router/rounding`olduğunda, iletilerin her iki uç noktaya yönlendirilmesine neden olan bir yönlendirme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

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

### <a name="soap-processing"></a><span data-ttu-id="3f6c1-163">SOAP Işleme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-163">SOAP Processing</span></span>

<span data-ttu-id="3f6c1-164">Farklı protokoller arasında ileti yönlendirmeyi desteklemek için, varsayılan olarak **RoutingBehavior** , iletilerin yönlendirildiği tüm istemci uç noktaları için <xref:System.ServiceModel.Routing.SoapProcessingBehavior> ekler.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="3f6c1-165">Bu davranış, iletiyi uç noktaya yönlendirmeden önce otomatik olarak yeni bir **MessageVersion** oluşturur, Ayrıca, istenen istemci uygulamasına döndürmeden önce herhangi bir yanıt belgesi için uyumlu bir **MessageVersion** oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="3f6c1-166">Giden ileti için yeni bir **MessageVersion** oluşturmak için uygulanan adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3f6c1-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="3f6c1-167">**İstek işleme**</span><span class="sxs-lookup"><span data-stu-id="3f6c1-167">**Request processing**</span></span>

- <span data-ttu-id="3f6c1-168">Giden bağlamanın/kanalın **MessageVersion** 'ı alın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="3f6c1-169">Özgün ileti için gövde okuyucuyu alın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-169">Get the body reader for the original message.</span></span>

- <span data-ttu-id="3f6c1-170">Aynı eylem, gövde okuyucu ve yeni bir **MessageVersion**ile yeni bir ileti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="3f6c1-171"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**Ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="3f6c1-172">Tüm ileti özelliklerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-172">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="3f6c1-173">Yanıtı işlerken kullanılacak özgün istek iletisini depolayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-173">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="3f6c1-174">Yeni istek iletisini döndürün.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-174">Return the new request message.</span></span>

<span data-ttu-id="3f6c1-175">**Yanıt işleme**</span><span class="sxs-lookup"><span data-stu-id="3f6c1-175">**Response processing**</span></span>

- <span data-ttu-id="3f6c1-176">Özgün istek iletisinin **MessageVersion** 'sini alın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-176">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="3f6c1-177">Alınan yanıt iletisi için gövde okuyucuyu alın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-177">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="3f6c1-178">Aynı eylem, gövde okuyucu ve özgün istek iletisinin **MessageVersion** ile yeni bir yanıt iletisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="3f6c1-179"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **Addressing. None**Ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="3f6c1-180">İleti özelliklerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-180">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="3f6c1-181">Yeni yanıt iletisini döndürün.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-181">Return the new response message.</span></span>

<span data-ttu-id="3f6c1-182">Varsayılan olarak, **SoapProcessingBehavior** , hizmet başladığında <xref:System.ServiceModel.Routing.RoutingBehavior> tarafından istemci uç noktalarına otomatik olarak eklenir; Ancak, <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliğini kullanarak SOAP işlemenin tüm istemci uç noktalarına eklenip eklenmeyeceğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="3f6c1-183">Ayrıca, daha ayrıntılı bir SOAP işleme denetimi gerekiyorsa, davranışı doğrudan belirli bir uç noktaya ekleyebilir ve uç nokta düzeyinde bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="3f6c1-184">SOAP işleme, özgün istek iletisinden farklı bir MessageVersion gerektiren bir uç nokta için devre dışı bırakılmışsa, iletiyi ileti gönderilmeden önce gereken SOAP değişikliklerinin gerçekleştirilmesi için özel bir mekanizma sağlamanız gerekir. hedef uç nokta.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="3f6c1-185">Aşağıdaki örneklerde **SoapProcessingEnabled** özelliği, **SoapProcessingBehavior** 'ın tüm istemci uç noktalarına otomatik olarak eklenmesini engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

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

### <a name="dynamic-configuration"></a><span data-ttu-id="3f6c1-186">Dinamik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f6c1-186">Dynamic Configuration</span></span>

<span data-ttu-id="3f6c1-187">Ek istemci uç noktaları eklediğinizde veya iletileri yönlendirmek için kullanılan filtreleri değiştirmeniz gerekiyorsa, hizmetin Şu anda iletileri aldığı uç noktalara engel olmak için yapılandırmayı çalışma zamanında dinamik olarak güncelleştirmeniz için bir yola sahip olmanız gerekir. Yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="3f6c1-188">Bir yapılandırma dosyasını veya ana bilgisayar uygulamasının kodunu değiştirmek her zaman yeterli değildir çünkü her iki yöntem de uygulamanın geri dönüşümünü gerektirir, bu da şu anda aktarımda olan iletilerin olası kaybına ve kapalı kalma süresine yol açabilir. hizmetin yeniden başlatılması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="3f6c1-189">**RoutingConfiguration** 'ı yalnızca programlı olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="3f6c1-190">Hizmeti bir yapılandırma dosyası kullanarak ilk olarak yapılandırabilmeniz mümkün olsa da, yalnızca yeni bir **RoutingConfiguration** oluşturarak ve onu <xref:System.ServiceModel.Routing.RoutingExtension> hizmeti uzantısı tarafından sunulan <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> metoduna parametre olarak geçirerek yapılandırmayı çalışma zamanında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="3f6c1-191">Şu anda yoldaki tüm iletiler önceki yapılandırma kullanılarak yönlendirilmeye devam ederken, **ApplyConfiguration** çağrısından sonra alınan iletiler yeni yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="3f6c1-192">Aşağıdaki örnek, yönlendirme hizmeti 'nin bir örneğini oluşturmayı ve sonra yapılandırmayı değiştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

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
> <span data-ttu-id="3f6c1-193">Yönlendirme hizmeti bu şekilde güncelleştirilirken yalnızca yeni bir yapılandırma geçirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="3f6c1-194">Geçerli yapılandırmanın yalnızca seçim öğelerini değiştirmek veya geçerli yapılandırmaya yeni girişler eklemek mümkün değildir; var olan bir yapılandırmayı oluşturup yeni bir yapılandırma geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="3f6c1-195">Önceki yapılandırma kullanılarak açılan oturumlar önceki yapılandırmayı kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="3f6c1-196">Yeni yapılandırma yalnızca yeni oturumlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-196">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="3f6c1-197">Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-197">Error Handling</span></span>

<span data-ttu-id="3f6c1-198">İleti gönderilmeye çalışılırken herhangi bir <xref:System.ServiceModel.CommunicationException> karşılaşılırsa, hata işleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="3f6c1-199">Bu özel durumlar genellikle <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>veya <xref:System.ServiceModel.CommunicationObjectFaultedException>gibi tanımlı istemci uç noktasıyla iletişim kurmaya çalışırken bir sorunla karşılaşıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="3f6c1-200">Hata işleme-kod ayrıca, **CommunicationException**'dan türetilmeyen başka bir ortak özel durum olan bir <xref:System.TimeoutException> gerçekleştiğinde göndermeyi yeniden denemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="3f6c1-201">Yukarıdaki özel durumlardan biri gerçekleştiğinde, yönlendirme hizmeti yedekleme uç noktaları listesine yük devreder.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="3f6c1-202">Tüm yedekleme uç noktaları bir iletişim hatasıyla başarısız olursa veya bir uç nokta hedef hizmette bir hata olduğunu gösteren bir özel durum döndürürse, yönlendirme hizmeti istemci uygulamasına bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="3f6c1-203">Hata işleme işlevselliği, bir ileti gönderilirken ve bir kanalı kapatmaya çalışırken oluşan özel durumları yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="3f6c1-204">Hata işleme kodu, iletişim kurduğu uygulama uç noktaları tarafından oluşturulan özel durumları algılamaya veya işlemeye yönelik değildir; bir hizmet tarafından oluşturulan <xref:System.ServiceModel.FaultException>, yönlendirme hizmetinde bir **FaultMessage** olarak görünür ve istemciye geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="3f6c1-205">Yönlendirme hizmeti bir iletiyi geçirmeye çalıştığında bir hata oluşursa, normalde yönlendirme hizmeti yokluğunda alacağınız bir <xref:System.ServiceModel.EndpointNotFoundException> yerine istemci tarafında <xref:System.ServiceModel.FaultException> alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="3f6c1-206">Bu nedenle, iç içe özel durumları incelemeden bir yönlendirme hizmeti özel durumları maskeleyebilir ve tam saydamlık sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="3f6c1-207">Özel durumları izleme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-207">Tracing Exceptions</span></span>

<span data-ttu-id="3f6c1-208">Bir listedeki uç noktaya ileti gönderilirken, yönlendirme hizmeti elde edilen özel durum verilerini izler ve özel durum ayrıntılarını özel **durumlar**adlı bir ileti özelliği olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="3f6c1-209">Bu, özel durum verilerini korur ve bir kullanıcı tarafından ileti denetçisi aracılığıyla programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="3f6c1-210">Özel durum verileri, bir ileti gönderilmeye çalışırken karşılaşılan özel durum ayrıntılarıyla eşleşen bir sözlükte ileti başına depolanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="3f6c1-211">Yedekleme uç noktaları</span><span class="sxs-lookup"><span data-stu-id="3f6c1-211">Backup Endpoints</span></span>

<span data-ttu-id="3f6c1-212">Filtre tablosu içindeki her bir filtre girişi, isteğe bağlı olarak, birincil uç noktaya gönderilirken bir iletim hatası durumunda kullanılan yedekleme uç noktaları listesini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="3f6c1-213">Böyle bir hata oluşursa, yönlendirme hizmeti iletiyi yedekleme uç noktası listesindeki ilk girişe aktarmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="3f6c1-214">Bu gönderme girişimi de bir iletim hatasıyla karşılaşırsa, yedekleme listesindeki bir sonraki uç nokta denenir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="3f6c1-215">Yönlendirme hizmeti, ileti başarılı bir şekilde alınana kadar iletiyi listedeki her bir uç noktaya göndermeye devam eder, tüm uç noktalar bir iletim hatası döndürmez veya bir uç nokta tarafından iletim dışı bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="3f6c1-216">Aşağıdaki örnekler, yönlendirme hizmetini bir yedekleme listesi kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-216">The following examples configure the Routing Service to use a backup list.</span></span>

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

### <a name="supported-error-patterns"></a><span data-ttu-id="3f6c1-217">Desteklenen hata desenleri</span><span class="sxs-lookup"><span data-stu-id="3f6c1-217">Supported Error Patterns</span></span>

<span data-ttu-id="3f6c1-218">Aşağıdaki tabloda, yedekleme uç noktası listelerinin kullanımıyla uyumlu desenler ve belirli desenler için hata işlemenin ayrıntılarını açıklayan notlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="3f6c1-219">Desen</span><span class="sxs-lookup"><span data-stu-id="3f6c1-219">Pattern</span></span>|<span data-ttu-id="3f6c1-220">Oturum</span><span class="sxs-lookup"><span data-stu-id="3f6c1-220">Session</span></span>|<span data-ttu-id="3f6c1-221">İşlem</span><span class="sxs-lookup"><span data-stu-id="3f6c1-221">Transaction</span></span>|<span data-ttu-id="3f6c1-222">Alma bağlamı</span><span class="sxs-lookup"><span data-stu-id="3f6c1-222">Receive Context</span></span>|<span data-ttu-id="3f6c1-223">Yedekleme listesi destekleniyor</span><span class="sxs-lookup"><span data-stu-id="3f6c1-223">Backup List Supported</span></span>|<span data-ttu-id="3f6c1-224">Notlar</span><span class="sxs-lookup"><span data-stu-id="3f6c1-224">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="3f6c1-225">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-225">One-Way</span></span>||||<span data-ttu-id="3f6c1-226">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-226">Yes</span></span>|<span data-ttu-id="3f6c1-227">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="3f6c1-228">Bu ileti çok noktaya yayın ise, yalnızca başarısız olan kanaldaki ileti yedekleme hedefine taşınır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="3f6c1-229">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-229">One-Way</span></span>||<span data-ttu-id="3f6c1-230">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-230">✔️</span></span>||<span data-ttu-id="3f6c1-231">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f6c1-231">No</span></span>|<span data-ttu-id="3f6c1-232">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-232">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="3f6c1-233">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-233">One-Way</span></span>|||<span data-ttu-id="3f6c1-234">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-234">✔️</span></span>|<span data-ttu-id="3f6c1-235">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-235">Yes</span></span>|<span data-ttu-id="3f6c1-236">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="3f6c1-237">İleti başarıyla alındıktan sonra tüm alma bağlamlarını doldurun.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="3f6c1-238">İleti herhangi bir uç nokta tarafından başarıyla alınmıyorsa, alma bağlamını tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="3f6c1-239">Bu ileti çok noktaya yayın olduğunda, alma bağlamı yalnızca ileti en az bir uç nokta (birincil veya yedek) tarafından başarıyla alınmışsa tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="3f6c1-240">Çok noktaya yayın yollarındaki uç noktaların hiçbiri iletiyi başarıyla aldıysanız, alma bağlamını tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="3f6c1-241">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-241">One-Way</span></span>||<span data-ttu-id="3f6c1-242">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-242">✔️</span></span>|<span data-ttu-id="3f6c1-243">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-243">✔️</span></span>|<span data-ttu-id="3f6c1-244">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-244">Yes</span></span>|<span data-ttu-id="3f6c1-245">Önceki işlemi iptal edin, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="3f6c1-246">Bir hatayla karşılaşan iletiler bir yedekleme hedefine iletilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="3f6c1-247">Tüm iletimlerin başarılı olduğu bir işlem oluşturulduktan sonra alma bağlamlarını tamamlayıp işlemi yürütün.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="3f6c1-248">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-248">One-Way</span></span>|<span data-ttu-id="3f6c1-249">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-249">✔️</span></span>|||<span data-ttu-id="3f6c1-250">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-250">Yes</span></span>|<span data-ttu-id="3f6c1-251">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="3f6c1-252">Çok noktaya yayın senaryosunda yalnızca bir oturumdaki veya oturum kapatma başarısız olan bir oturumdaki iletiler yedekleme hedeflerine yeniden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="3f6c1-253">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-253">One-Way</span></span>|<span data-ttu-id="3f6c1-254">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-254">✔️</span></span>|<span data-ttu-id="3f6c1-255">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-255">✔️</span></span>||<span data-ttu-id="3f6c1-256">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f6c1-256">No</span></span>|<span data-ttu-id="3f6c1-257">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-257">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="3f6c1-258">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-258">One-Way</span></span>|<span data-ttu-id="3f6c1-259">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-259">✔️</span></span>||<span data-ttu-id="3f6c1-260">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-260">✔️</span></span>|<span data-ttu-id="3f6c1-261">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-261">Yes</span></span>|<span data-ttu-id="3f6c1-262">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="3f6c1-263">Tüm iletiler hatasız tamamlandı, oturum daha fazla ileti olmadığını ve yönlendirme hizmeti tüm giden oturum kanallarını başarıyla kapatmışsa, tüm alma bağlamlarının tamamlandığı ve gelen oturum kanalının kapalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="3f6c1-264">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-264">One-Way</span></span>|<span data-ttu-id="3f6c1-265">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-265">✔️</span></span>|<span data-ttu-id="3f6c1-266">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-266">✔️</span></span>|<span data-ttu-id="3f6c1-267">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-267">✔️</span></span>|<span data-ttu-id="3f6c1-268">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-268">Yes</span></span>|<span data-ttu-id="3f6c1-269">Geçerli işlemi iptal edin ve yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="3f6c1-270">Oturumdaki tüm önceki iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="3f6c1-271">Tüm iletilerin başarıyla gönderildiği ve oturum daha fazla ileti olmadığını gösterdiği bir işlem oluşturulduktan sonra, tüm giden oturum kanalları kapatılır, alma bağlamlarının tümü işlemle tamamlanır, gelen oturum kanalı kapalı ve işlem kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="3f6c1-272">Oturumlar çok noktaya yayın yaparken, hatasız bir hata olmayan mesajlar daha önce olduğu gibi aynı hedefe gönderilir ve bir hatayla karşılaşan iletiler yedekleme hedeflerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="3f6c1-273">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-273">Two-Way</span></span>||||<span data-ttu-id="3f6c1-274">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-274">Yes</span></span>|<span data-ttu-id="3f6c1-275">Bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-275">Send to a backup destination.</span></span>  <span data-ttu-id="3f6c1-276">Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-276">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="3f6c1-277">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-277">Two-Way</span></span>|<span data-ttu-id="3f6c1-278">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-278">✔️</span></span>|||<span data-ttu-id="3f6c1-279">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-279">Yes</span></span>|<span data-ttu-id="3f6c1-280">Kanaldaki tüm iletileri bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="3f6c1-281">Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-281">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="3f6c1-282">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-282">Two-Way</span></span>||<span data-ttu-id="3f6c1-283">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-283">✔️</span></span>||<span data-ttu-id="3f6c1-284">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f6c1-284">No</span></span>|<span data-ttu-id="3f6c1-285">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-285">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="3f6c1-286">İki yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-286">Two-Way</span></span>|<span data-ttu-id="3f6c1-287">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-287">✔️</span></span>|<span data-ttu-id="3f6c1-288">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-288">✔️</span></span>||<span data-ttu-id="3f6c1-289">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f6c1-289">No</span></span>|<span data-ttu-id="3f6c1-290">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-290">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="3f6c1-291">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-291">Duplex</span></span>||||<span data-ttu-id="3f6c1-292">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f6c1-292">No</span></span>|<span data-ttu-id="3f6c1-293">Oturum olmayan çift yönlü iletişim şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-293">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="3f6c1-294">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="3f6c1-294">Duplex</span></span>|<span data-ttu-id="3f6c1-295">✔ ︎</span><span class="sxs-lookup"><span data-stu-id="3f6c1-295">✔️</span></span>|||<span data-ttu-id="3f6c1-296">Evet</span><span class="sxs-lookup"><span data-stu-id="3f6c1-296">Yes</span></span>|<span data-ttu-id="3f6c1-297">Bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-297">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="3f6c1-298">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3f6c1-298">Hosting</span></span>

<span data-ttu-id="3f6c1-299">Yönlendirme hizmeti bir WCF hizmeti olarak uygulandığından, bir uygulama içinde kendi kendine barındırılan veya IIS ya da WAS tarafından barındırılan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="3f6c1-300">Bu barındırma ortamlarında sunulan otomatik başlatma ve yaşam döngüsü yönetim özelliklerinden yararlanmak için yönlendirme hizmetinin IIS, WAS veya bir Windows hizmet uygulamasında barındırılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="3f6c1-301">Aşağıdaki örnek, bir uygulamada yönlendirme hizmetinin barındırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-301">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="3f6c1-302">Yönlendirme hizmetini IIS veya WAS içinde barındırmak için bir hizmet dosyası (. svc) oluşturmanız ya da hizmetin yapılandırma tabanlı etkinleştirmesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="3f6c1-303">Bir hizmet dosyası kullanırken, hizmet parametresini kullanarak <xref:System.ServiceModel.Routing.RoutingService> belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="3f6c1-304">Aşağıdaki örnek, yönlendirme hizmetini IIS veya WAS ile barındırmak için kullanılabilecek örnek bir hizmet dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="3f6c1-305">Yönlendirme hizmeti ve kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-305">Routing Service and Impersonation</span></span>

<span data-ttu-id="3f6c1-306">WCF yönlendirme hizmeti, hem gönderme hem de alma iletileri için kimliğe bürünme ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="3f6c1-307">Kimliğe bürünme için tüm olağan Windows kısıtlamaları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="3f6c1-308">Kendi hizmetinizi yazarken kimliğe bürünme özelliğini kullanmak üzere hizmet veya hesap izinleri ayarlamanız gerekiyorsa, yönlendirme hizmeti ile kimliğe bürünme özelliğini kullanmak için bu adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="3f6c1-309">Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="3f6c1-310">Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET uyumluluk modundayken ASP.NET Kimliğe bürünme özelliğinin kullanımını veya kimliğe bürünmeye izin verecek şekilde yapılandırılmış Windows kimlik bilgilerinin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="3f6c1-311">ASP.NET uyumluluk modu hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="3f6c1-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="3f6c1-312">WCF yönlendirme hizmeti temel kimlik doğrulamasıyla kimliğe bürünme özelliğini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="3f6c1-313">Yönlendirme hizmeti ile ASP.NET Kimliğe bürünme özelliğini kullanmak için hizmet barındırma ortamında ASP.NET uyumluluk modunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="3f6c1-314">Yönlendirme hizmeti zaten ASP.NET uyumluluk moduna izin vermek üzere işaretlendi ve kimliğe bürünme otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="3f6c1-315">Kimliğe bürünme, ASP.NET tümleştirmesi 'nin yönlendirme hizmeti ile desteklenen tek kullanımı.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="3f6c1-316">Windows kimlik bilgisi kimliğe bürünme özelliğini yönlendirme hizmeti ile birlikte kullanmak için hem kimlik bilgilerini hem de hizmeti yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="3f6c1-317"><xref:System.ServiceModel.ChannelFactory>tarafından çözümlenemeyen istemci kimlik bilgileri nesnesi (<xref:System.ServiceModel.Security.WindowsClientCredential>, kimliğe bürünmeye izin vermek için ayarlanması gereken bir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="3f6c1-318">Son olarak, hizmette `true``ImpersonateCallerForAllOperations` ayarlamak için <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> davranışını yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="3f6c1-319">Yönlendirme hizmeti, kimliğe bürünme özelliği etkinken iletileri iletmek için istemciler oluşturulup oluşturulmayacağını belirlemek için bu bayrağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f6c1-320">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f6c1-320">See also</span></span>

- [<span data-ttu-id="3f6c1-321">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="3f6c1-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="3f6c1-322">Anlaşmaları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="3f6c1-323">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="3f6c1-323">Choosing a Filter</span></span>](choosing-a-filter.md)
