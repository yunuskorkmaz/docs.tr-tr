---
description: 'Daha fazla bilgi edinin: yönlendirme tanıtımı'
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 86f5b5dcc0bea067ac3dcfc8a87331da42c642aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779900"
---
# <a name="routing-introduction"></a><span data-ttu-id="fbd45-103">Yönlendirme Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="fbd45-103">Routing Introduction</span></span>

<span data-ttu-id="fbd45-104">Yönlendirme hizmeti ileti içeriğine göre iletileri yönlendirme yeteneğine sahip genel bir takılabilir SOAP aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-104">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="fbd45-105">Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelik yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolar uygulamanıza olanak tanıyan karmaşık yönlendirme mantığı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-105">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="fbd45-106">Yönlendirme hizmeti Ayrıca, birincil hedef uç noktasına gönderilirken bir hata oluşursa gönderilecek olan yedekleme uç noktaları listesini ayarlamanıza olanak tanıyan hata işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-106">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="fbd45-107">Bu konu, yönlendirme hizmeti için yeni olanlar için tasarlanmıştır ve temel yapılandırmayı ve yönlendirme hizmetinin barındırılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-107">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="fbd45-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbd45-108">Configuration</span></span>

<span data-ttu-id="fbd45-109">Yönlendirme hizmeti, istemci uygulamalarından ileti alan ve iletileri bir veya daha fazla hedef uç noktaya yönlendiren bir veya daha fazla hizmet uç noktası sunan bir WCF hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-109">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="fbd45-110">Hizmet <xref:System.ServiceModel.Routing.RoutingBehavior> , hizmet tarafından sunulan hizmet uç noktalarına uygulanan bir sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-110">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="fbd45-111">Bu davranış, hizmetin nasıl çalıştığı hakkında çeşitli yönleri yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-111">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="fbd45-112">Yapılandırma dosyası kullanılırken yapılandırma kolaylığı için, parametreler **RoutingBehavior** üzerinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-112">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="fbd45-113">Kod tabanlı senaryolarda, bu parametreler bir nesnenin parçası olarak belirtilir <xref:System.ServiceModel.Routing.RoutingConfiguration> ve daha sonra bir **RoutingBehavior**'a geçirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="fbd45-113">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="fbd45-114">Bu davranış, başlatıldığında, <xref:System.ServiceModel.Routing.SoapProcessingBehavior> istemci uç noktalarına ILETILERIN SOAP işlemesini gerçekleştirmek için kullanılan öğesini ekler.</span><span class="sxs-lookup"><span data-stu-id="fbd45-114">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="fbd45-115">Bu, yönlendirme hizmetinin ileti alındığı uç noktadan farklı bir **MessageVersion** gerektiren uç noktalara ileti aktarmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-115">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="fbd45-116">**RoutingBehavior** Ayrıca, <xref:System.ServiceModel.Routing.RoutingExtension> çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için bir erişilebilirlik noktası sağlayan bir hizmet uzantısı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fbd45-116">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="fbd45-117">**RoutingConfiguration** sınıfı, yönlendirme hizmeti yapılandırmasını yapılandırmak ve güncelleştirmek için tutarlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-117">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="fbd45-118">Yönlendirme hizmeti için ayarlar olarak davranan ve hizmet başlatıldığında **RoutingBehavior** 'ı yapılandırmak için kullanılan ve çalışma zamanında yönlendirme yapılandırmasını değiştirmek Için **RoutingExtension** 'a geçirilen parametreleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-118">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="fbd45-119">İletilerin içerik tabanlı yönlendirilmesini gerçekleştirmek için kullanılan yönlendirme mantığı, birden çok <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneyi filtre tablolarında (nesneler) birlikte gruplandırarak tanımlanır <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-119">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="fbd45-120">Gelen iletiler, filtre tablosunda bulunan ileti filtrelerine ve bir hedef uç noktaya iletilen iletiyle eşleşen her **MessageFilter** için değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-120">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="fbd45-121">İletileri yönlendirmek için kullanılması gereken filtre tablosu, yapılandırma veya **RoutingConfiguration** nesnesi kullanılarak kod aracılığıyla yönlendirme **davranışı** kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-121">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="fbd45-122">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="fbd45-122">Defining Endpoints</span></span>

<span data-ttu-id="fbd45-123">Kullanacağınız yönlendirme mantığını tanımlayarak yapılandırmanızı başlatmanız gerektiği gibi görünse de, ilk adımınız ileti yönlendirdiğiniz uç noktaların şeklini belirlemektir, gerçekten yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-123">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="fbd45-124">Yönlendirme hizmeti, iletileri almak ve göndermek için kullanılan kanalların şeklini tanımlayan sözleşmeleri kullanır ve bu nedenle, giriş kanalının şekli çıkış kanalının ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-124">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="fbd45-125">Örneğin, istek-yanıt kanalı şeklini kullanan uç noktalara yönlendirmeniz durumunda, gelen uç noktalarında, gibi uyumlu bir anlaşma kullanmanız gerekir <xref:System.ServiceModel.Routing.IRequestReplyRouter> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-125">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="fbd45-126">Yani, hedef uç noktalarınız birden çok iletişim deseniyle (tek yönlü ve iki yönlü işlemleri karıştırma gibi) sözleşmeler kullanıyorsa, bunlara ileti alabilen ve bunlara yönlendirebileceği tek bir hizmet uç noktası oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fbd45-126">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="fbd45-127">Hangi uç noktaların uyumlu şekillere sahip olduğunu ve hedef uç noktalara yönlendirilmek üzere ileti almak için kullanılacak bir veya daha fazla hizmet uç noktası tanımlanacağını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-127">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd45-128">Birden çok iletişim deseni (tek yönlü ve iki yönlü işlemlerin karışımı gibi) belirten sözleşmelerle çalışırken, bir geçici çözüm, yönlendirme hizmetinde, gibi bir çift yönlü sözleşme kullanmaktır <xref:System.ServiceModel.Routing.IDuplexSessionRouter> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-128">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="fbd45-129">Ancak bu, bağlamanın çift yönlü iletişim özelliği olması gerektiği anlamına gelir. Bu, tüm senaryolarda mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-129">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="fbd45-130">Bunun mümkün olmadığı senaryolarda, iletişimin birden çok uç noktaya düzenleme veya uygulamanın değiştirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-130">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="fbd45-131">Yönlendirme sözleşmeleri hakkında daha fazla bilgi için bkz. [yönlendirme sözleşmeleri](routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="fbd45-131">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="fbd45-132">Hizmet uç noktası tanımlandıktan sonra, belirli bir **RoutingConfiguration** 'ı uç noktayla Ilişkilendirmek Için **RoutingBehavior** 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-132">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="fbd45-133">Yönlendirme hizmetini bir yapılandırma dosyası kullanarak yapılandırırken, bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığını içeren filtre tablosunu belirtmek için **RoutingBehavior** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-133">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="fbd45-134">Yönlendirme hizmetini programlı olarak yapılandırıyorsanız, **RoutingConfiguration** kullanarak filtre tablosunu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-134">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="fbd45-135">Aşağıdaki örnek, yönlendirme hizmeti tarafından hem programlı olarak hem de bir yapılandırma dosyası kullanılarak kullanılan hizmet ve istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-135">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

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

<span data-ttu-id="fbd45-136">Bu örnek, yönlendirme hizmetini `http://localhost:8000/routingservice/router` yönlendirilen iletileri almak için kullanılan adresine sahip tek bir uç noktayı kullanıma sunmak üzere yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-136">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="fbd45-137">İletiler istek-yanıt uç noktalarına yönlendirildiğinden, hizmet uç noktası <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-137">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="fbd45-138">Bu yapılandırma ayrıca iletilerin yönlendirildiği tek bir istemci uç noktasını tanımlar `http://localhost:8000/servicemodelsample/service` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-138">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="fbd45-139">"RoutingTable1" adlı Filtre tablosu (gösterilmez), iletileri yönlendirmek için kullanılan yönlendirme mantığını içerir ve **RoutingBehavior** (bir yapılandırma dosyası için) veya **RoutingConfiguration** (programlı yapılandırma için) kullanılarak hizmet uç noktasıyla ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-139">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="fbd45-140">Yönlendirme mantığı</span><span class="sxs-lookup"><span data-stu-id="fbd45-140">Routing Logic</span></span>

<span data-ttu-id="fbd45-141">İletileri yönlendirmek için kullanılan yönlendirme mantığını tanımlamak için, gelen iletilerde bulunan verilerin üzerinde benzersiz olarak işlem yapabileceğini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-141">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="fbd45-142">Örneğin, tüm hedef uç noktaları aynı SOAP eylemlerini paylaşmak üzere yönlendirdiğiniz takdirde, ileti içinde yer alan eylemin değeri iletinin hangi belirli uç noktada yönlendirildiğini belirten iyi bir göstergedir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-142">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="fbd45-143">İletileri belirli bir uç noktaya benzersiz bir şekilde yönlendirmelisiniz, iletinin yönlendirildiği hedef uç noktayı benzersiz şekilde tanımlayan verileri filtrelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-143">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="fbd45-144">Yönlendirme hizmeti, ileti içindeki adres, eylem, uç nokta adı ve hatta bir XPath sorgusu gibi belirli değerleri denetleyen çeşitli **MessageFilter** uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-144">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="fbd45-145">Bu uygulamalardan hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir **MessageFilter** uygulaması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-145">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="fbd45-146">İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaların karşılaştırması hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md) ve [bir filtre seçme](choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="fbd45-146">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="fbd45-147">Birden çok ileti filtresi, her **MessageFilter** öğesini bir hedef uç noktasıyla ilişkilendiren filtre tablolarında birlikte düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-147">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="fbd45-148">İsteğe bağlı olarak, bir aktarım hatası durumunda yönlendirme hizmetinin iletiyi göndermek için deneyeceği yedek uç noktaların listesini belirtmek için filtre tablosu da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-148">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="fbd45-149">Varsayılan olarak, bir filtre tablosu içindeki tüm ileti filtreleri aynı anda değerlendirilir; Ancak, <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> ileti filtrelerinin belirli bir sırada değerlendirilmesini sağlayan bir de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-149">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="fbd45-150">En yüksek önceliğe sahip tüm girişler önce değerlendirilir ve daha yüksek bir öncelik düzeyinde eşleşme bulunursa düşük önceliklerdeki ileti filtreleri değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="fbd45-150">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="fbd45-151">Filtre tabloları hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="fbd45-151">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="fbd45-152">Aşağıdaki örneklerde, <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> tüm iletiler için değerlendirilen ' kullanılır `true` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-152">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="fbd45-153">Bu **MessageFilter** , "routingTable1" filtre tablosuna eklenir ve bu, **MessageFilter** öğesini "hesaplatorservice" adlı istemci uç noktasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-153">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="fbd45-154">**RoutingBehavior** daha sonra bu tablonun hizmet uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-154">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

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
> <span data-ttu-id="fbd45-155">Varsayılan olarak, yönlendirme hizmeti yalnızca iletinin üstbilgilerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-155">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="fbd45-156">Filtrelerin ileti gövdesine erişmesine izin vermek için, olarak ayarlamanız gerekir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-156">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="fbd45-157">**Noktalı**</span><span class="sxs-lookup"><span data-stu-id="fbd45-157">**Multicast**</span></span>

<span data-ttu-id="fbd45-158">Birçok yönlendirme hizmeti yapılandırması iletileri yalnızca belirli bir uç noktaya yönlendiren özel durum filtre mantığı kullanır, ancak belirli bir iletiyi birden çok hedef uç noktaya yönlendirmenize gerek vardır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-158">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="fbd45-159">Bir iletinin birden çok hedefe çok noktaya yayını olması için aşağıdaki koşulların doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="fbd45-159">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="fbd45-160">İstek yanıtındaki istemci uygulaması tarafından yalnızca bir yanıt alınabileceğinden, kanal şeklinin istek Yanıtla (ancak tek yönlü veya çift yönlü olabilir) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-160">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="fbd45-161">İleti değerlendirilirken birden çok filtrenin dönmesi gerekir `true` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-161">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="fbd45-162">Bu koşullar karşılanıyorsa ileti, ' i değerlendiren tüm filtrelerin tüm uç noktalarına yönlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-162">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="fbd45-163">Aşağıdaki örnek, iletideki bitiş noktası adresi olduğunda, iletilerin her iki uç noktaya yönlendirilmesine neden olan bir yönlendirme yapılandırmasını tanımlar `http://localhost:8000/routingservice/router/rounding` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-163">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

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

### <a name="soap-processing"></a><span data-ttu-id="fbd45-164">SOAP Işleme</span><span class="sxs-lookup"><span data-stu-id="fbd45-164">SOAP Processing</span></span>

<span data-ttu-id="fbd45-165">Farklı protokoller arasında ileti yönlendirmeyi desteklemek için, varsayılan olarak **RoutingBehavior** , <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletilerinin yönlendirildiği tüm istemci uç noktalara ekler.</span><span class="sxs-lookup"><span data-stu-id="fbd45-165">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="fbd45-166">Bu davranış, iletiyi uç noktaya yönlendirmeden önce otomatik olarak yeni bir **MessageVersion** oluşturur, Ayrıca, istenen istemci uygulamasına döndürmeden önce herhangi bir yanıt belgesi için uyumlu bir **MessageVersion** oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fbd45-166">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="fbd45-167">Giden ileti için yeni bir **MessageVersion** oluşturmak için uygulanan adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fbd45-167">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="fbd45-168">**İstek işleme**</span><span class="sxs-lookup"><span data-stu-id="fbd45-168">**Request processing**</span></span>

- <span data-ttu-id="fbd45-169">Giden bağlamanın/kanalın **MessageVersion** 'ı alın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-169">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="fbd45-170">Özgün ileti için gövde okuyucuyu alın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-170">Get the body reader for the original message.</span></span>

- <span data-ttu-id="fbd45-171">Aynı eylem, gövde okuyucu ve yeni bir **MessageVersion** ile yeni bir ileti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbd45-171">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="fbd45-172">Eğer <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None** ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-172">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="fbd45-173">Tüm ileti özelliklerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-173">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="fbd45-174">Yanıtı işlerken kullanılacak özgün istek iletisini depolayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-174">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="fbd45-175">Yeni istek iletisini döndürün.</span><span class="sxs-lookup"><span data-stu-id="fbd45-175">Return the new request message.</span></span>

<span data-ttu-id="fbd45-176">**Yanıt işleme**</span><span class="sxs-lookup"><span data-stu-id="fbd45-176">**Response processing**</span></span>

- <span data-ttu-id="fbd45-177">Özgün istek iletisinin **MessageVersion** 'sini alın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-177">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="fbd45-178">Alınan yanıt iletisi için gövde okuyucuyu alın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-178">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="fbd45-179">Aynı eylem, gövde okuyucu ve özgün istek iletisinin **MessageVersion** ile yeni bir yanıt iletisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbd45-179">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="fbd45-180">Eğer <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None** ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-180">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="fbd45-181">İleti özelliklerini yeni iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-181">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="fbd45-182">Yeni yanıt iletisini döndürün.</span><span class="sxs-lookup"><span data-stu-id="fbd45-182">Return the new response message.</span></span>

<span data-ttu-id="fbd45-183">Varsayılan olarak, **SoapProcessingBehavior** , hizmet başladığında istemci uç noktalarına otomatik olarak eklenir <xref:System.ServiceModel.Routing.RoutingBehavior> ; ancak, özelliğini kullanarak soap işlemenin tüm istemci uç noktalarına eklenip eklenmeyeceğini denetleyebilirsiniz <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-183">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="fbd45-184">Ayrıca, daha ayrıntılı bir SOAP işleme denetimi gerekiyorsa, davranışı doğrudan belirli bir uç noktaya ekleyebilir ve uç nokta düzeyinde bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-184">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd45-185">SOAP işleme, özgün istek iletisinden farklı bir MessageVersion gerektiren bir uç nokta için devre dışıysa, iletiyi hedef uç noktaya göndermeden önce gereken SOAP değişikliklerinin gerçekleştirilmesi için özel bir mekanizma sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-185">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="fbd45-186">Aşağıdaki örneklerde **SoapProcessingEnabled** özelliği, **SoapProcessingBehavior** 'ın tüm istemci uç noktalarına otomatik olarak eklenmesini engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-186">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

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

### <a name="dynamic-configuration"></a><span data-ttu-id="fbd45-187">Dinamik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbd45-187">Dynamic Configuration</span></span>

<span data-ttu-id="fbd45-188">Ek istemci uç noktaları eklediğinizde veya iletileri yönlendirmek için kullanılan filtreleri değiştirmeniz gerekiyorsa, hizmetin yönlendirme hizmeti aracılığıyla iletileri aldığı uç noktalara engel olmak için yapılandırmayı çalışma zamanında dinamik olarak güncelleştirmeniz için bir yola sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-188">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="fbd45-189">Bir yapılandırma dosyasını veya ana bilgisayar uygulamasının kodunu değiştirmek her zaman yeterli değildir, çünkü herhangi bir yöntem uygulamanın geri dönüşümünü gerektirir, bu da şu anda aktarımda olan iletilerin olası kaybına ve hizmetin yeniden başlatılmasını beklerken kapalı kalma süresine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fbd45-189">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="fbd45-190">**RoutingConfiguration** 'ı yalnızca programlı olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-190">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="fbd45-191">Hizmeti bir yapılandırma dosyası kullanarak ilk olarak yapılandırabilmeniz mümkün olsa da, yalnızca yeni bir **RoutingConfiguration** oluşturup <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> hizmet uzantısının açığa çıkarılan yöntemine bir parametre olarak geçirerek yapılandırmayı çalışma zamanında değiştirebilirsiniz <xref:System.ServiceModel.Routing.RoutingExtension> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-191">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="fbd45-192">Şu anda yoldaki tüm iletiler önceki yapılandırma kullanılarak yönlendirilmeye devam ederken, **ApplyConfiguration** çağrısından sonra alınan iletiler yeni yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-192">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="fbd45-193">Aşağıdaki örnek, yönlendirme hizmeti 'nin bir örneğini oluşturmayı ve sonra yapılandırmayı değiştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-193">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

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
> <span data-ttu-id="fbd45-194">Yönlendirme hizmeti bu şekilde güncelleştirilirken yalnızca yeni bir yapılandırma geçirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fbd45-194">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="fbd45-195">Geçerli yapılandırmanın yalnızca seçim öğelerini değiştirmek veya geçerli yapılandırmaya yeni girişler eklemek mümkün değildir; var olan bir yapılandırmayı oluşturup yeni bir yapılandırma geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-195">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd45-196">Önceki yapılandırma kullanılarak açılan oturumlar önceki yapılandırmayı kullanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="fbd45-196">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="fbd45-197">Yeni yapılandırma yalnızca yeni oturumlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-197">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="fbd45-198">Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="fbd45-198">Error Handling</span></span>

<span data-ttu-id="fbd45-199"><xref:System.ServiceModel.CommunicationException>İleti gönderilmeye çalışılırken herhangi bir hatayla karşılaşırsanız, hata işleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-199">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="fbd45-200">Bu özel durumlar genellikle, veya gibi tanımlı istemci uç noktasıyla iletişim kurmaya çalışırken bir sorunla karşılaşıldığını gösterir <xref:System.ServiceModel.EndpointNotFoundException> <xref:System.ServiceModel.ServerTooBusyException> <xref:System.ServiceModel.CommunicationObjectFaultedException> .</span><span class="sxs-lookup"><span data-stu-id="fbd45-200">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="fbd45-201">Hata işleme-kod ayrıca, bir durum <xref:System.TimeoutException> oluştuğunda, **CommunicationException**'dan türetilmeyen başka bir ortak özel durum olduğunda göndermeyi yeniden denemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-201">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="fbd45-202">Yukarıdaki özel durumlardan biri gerçekleştiğinde, yönlendirme hizmeti yedekleme uç noktaları listesine yük devreder.</span><span class="sxs-lookup"><span data-stu-id="fbd45-202">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="fbd45-203">Tüm yedekleme uç noktaları bir iletişim hatasıyla başarısız olursa veya bir uç nokta hedef hizmette bir hata olduğunu gösteren bir özel durum döndürürse, yönlendirme hizmeti istemci uygulamasına bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbd45-203">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd45-204">Hata işleme işlevselliği, bir ileti gönderilirken ve bir kanalı kapatmaya çalışırken oluşan özel durumları yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="fbd45-204">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="fbd45-205">Hata işleme kodu, iletişim kurduğu uygulama uç noktaları tarafından oluşturulan özel durumları algılamaya veya işlemeye yönelik değildir; <xref:System.ServiceModel.FaultException> bir hizmet tarafından oluşturulan bir durum, yönlendirme hizmetinde bir **FaultMessage** olarak görünür ve istemciye geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-205">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="fbd45-206">Yönlendirme hizmeti bir iletiyi geçirmeye çalıştığında bir hata oluşursa, <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.EndpointNotFoundException> normalde yönlendirme hizmeti yokluğunda olmak yerine istemci tarafında bir alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-206">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="fbd45-207">Bu nedenle, iç içe özel durumları incelemeden bir yönlendirme hizmeti özel durumları maskeleyebilir ve tam saydamlık sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-207">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="fbd45-208">Özel durumları izleme</span><span class="sxs-lookup"><span data-stu-id="fbd45-208">Tracing Exceptions</span></span>

<span data-ttu-id="fbd45-209">Bir listedeki uç noktaya ileti gönderilirken, yönlendirme hizmeti elde edilen özel durum verilerini izler ve özel durum ayrıntılarını özel **durumlar** adlı bir ileti özelliği olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="fbd45-209">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="fbd45-210">Bu, özel durum verilerini korur ve bir kullanıcı tarafından ileti denetçisi aracılığıyla programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-210">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="fbd45-211">Özel durum verileri, bir ileti gönderilmeye çalışırken karşılaşılan özel durum ayrıntılarıyla eşleşen bir sözlükte ileti başına depolanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-211">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="fbd45-212">Yedekleme uç noktaları</span><span class="sxs-lookup"><span data-stu-id="fbd45-212">Backup Endpoints</span></span>

<span data-ttu-id="fbd45-213">Filtre tablosu içindeki her bir filtre girişi, isteğe bağlı olarak, birincil uç noktaya gönderilirken bir iletim hatası durumunda kullanılan yedekleme uç noktaları listesini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-213">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="fbd45-214">Böyle bir hata oluşursa, yönlendirme hizmeti iletiyi yedekleme uç noktası listesindeki ilk girişe aktarmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-214">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="fbd45-215">Bu gönderme girişimi de bir iletim hatasıyla karşılaşırsa, yedekleme listesindeki bir sonraki uç nokta denenir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-215">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="fbd45-216">Yönlendirme hizmeti, ileti başarılı bir şekilde alınana kadar iletiyi listedeki her bir uç noktaya göndermeye devam eder, tüm uç noktalar bir iletim hatası döndürmez veya bir uç nokta tarafından iletim dışı bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fbd45-216">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="fbd45-217">Aşağıdaki örnekler, yönlendirme hizmetini bir yedekleme listesi kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-217">The following examples configure the Routing Service to use a backup list.</span></span>

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

### <a name="supported-error-patterns"></a><span data-ttu-id="fbd45-218">Desteklenen hata desenleri</span><span class="sxs-lookup"><span data-stu-id="fbd45-218">Supported Error Patterns</span></span>

<span data-ttu-id="fbd45-219">Aşağıdaki tabloda, yedekleme uç noktası listelerinin kullanımıyla uyumlu desenler ve belirli desenler için hata işlemenin ayrıntılarını açıklayan notlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-219">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="fbd45-220">Desen</span><span class="sxs-lookup"><span data-stu-id="fbd45-220">Pattern</span></span>|<span data-ttu-id="fbd45-221">Oturum</span><span class="sxs-lookup"><span data-stu-id="fbd45-221">Session</span></span>|<span data-ttu-id="fbd45-222">İşlem</span><span class="sxs-lookup"><span data-stu-id="fbd45-222">Transaction</span></span>|<span data-ttu-id="fbd45-223">Alma bağlamı</span><span class="sxs-lookup"><span data-stu-id="fbd45-223">Receive Context</span></span>|<span data-ttu-id="fbd45-224">Yedekleme listesi destekleniyor</span><span class="sxs-lookup"><span data-stu-id="fbd45-224">Backup List Supported</span></span>|<span data-ttu-id="fbd45-225">Notlar</span><span class="sxs-lookup"><span data-stu-id="fbd45-225">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="fbd45-226">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-226">One-Way</span></span>||||<span data-ttu-id="fbd45-227">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-227">Yes</span></span>|<span data-ttu-id="fbd45-228">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-228">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="fbd45-229">Bu ileti çok noktaya yayın ise, yalnızca başarısız olan kanaldaki ileti yedekleme hedefine taşınır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-229">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="fbd45-230">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-230">One-Way</span></span>||<span data-ttu-id="fbd45-231">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-231">✔️</span></span>||<span data-ttu-id="fbd45-232">No</span><span class="sxs-lookup"><span data-stu-id="fbd45-232">No</span></span>|<span data-ttu-id="fbd45-233">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-233">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="fbd45-234">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-234">One-Way</span></span>|||<span data-ttu-id="fbd45-235">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-235">✔️</span></span>|<span data-ttu-id="fbd45-236">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-236">Yes</span></span>|<span data-ttu-id="fbd45-237">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-237">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="fbd45-238">İleti başarıyla alındıktan sonra tüm alma bağlamlarını doldurun.</span><span class="sxs-lookup"><span data-stu-id="fbd45-238">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="fbd45-239">İleti herhangi bir uç nokta tarafından başarıyla alınmıyorsa, alma bağlamını tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-239">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="fbd45-240">Bu ileti çok noktaya yayın olduğunda, alma bağlamı yalnızca ileti en az bir uç nokta (birincil veya yedek) tarafından başarıyla alınmışsa tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-240">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="fbd45-241">Çok noktaya yayın yollarındaki uç noktaların hiçbiri iletiyi başarıyla aldıysanız, alma bağlamını tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="fbd45-241">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="fbd45-242">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-242">One-Way</span></span>||<span data-ttu-id="fbd45-243">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-243">✔️</span></span>|<span data-ttu-id="fbd45-244">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-244">✔️</span></span>|<span data-ttu-id="fbd45-245">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-245">Yes</span></span>|<span data-ttu-id="fbd45-246">Önceki işlemi iptal edin, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-246">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="fbd45-247">Bir hatayla karşılaşan iletiler bir yedekleme hedefine iletilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-247">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="fbd45-248">Tüm iletimlerin başarılı olduğu bir işlem oluşturulduktan sonra alma bağlamlarını tamamlayıp işlemi yürütün.</span><span class="sxs-lookup"><span data-stu-id="fbd45-248">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="fbd45-249">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-249">One-Way</span></span>|<span data-ttu-id="fbd45-250">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-250">✔️</span></span>|||<span data-ttu-id="fbd45-251">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-251">Yes</span></span>|<span data-ttu-id="fbd45-252">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-252">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="fbd45-253">Çok noktaya yayın senaryosunda yalnızca bir oturumdaki veya oturum kapatma başarısız olan bir oturumdaki iletiler yedekleme hedeflerine yeniden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-253">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="fbd45-254">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-254">One-Way</span></span>|<span data-ttu-id="fbd45-255">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-255">✔️</span></span>|<span data-ttu-id="fbd45-256">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-256">✔️</span></span>||<span data-ttu-id="fbd45-257">No</span><span class="sxs-lookup"><span data-stu-id="fbd45-257">No</span></span>|<span data-ttu-id="fbd45-258">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-258">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="fbd45-259">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-259">One-Way</span></span>|<span data-ttu-id="fbd45-260">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-260">✔️</span></span>||<span data-ttu-id="fbd45-261">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-261">✔️</span></span>|<span data-ttu-id="fbd45-262">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-262">Yes</span></span>|<span data-ttu-id="fbd45-263">İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-263">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="fbd45-264">Tüm iletiler hatasız tamamlandı, oturum daha fazla ileti olmadığını ve yönlendirme hizmeti tüm giden oturum kanallarını başarıyla kapatmışsa, tüm alma bağlamlarının tamamlandığı ve gelen oturum kanalının kapalı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-264">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="fbd45-265">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-265">One-Way</span></span>|<span data-ttu-id="fbd45-266">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-266">✔️</span></span>|<span data-ttu-id="fbd45-267">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-267">✔️</span></span>|<span data-ttu-id="fbd45-268">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-268">✔️</span></span>|<span data-ttu-id="fbd45-269">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-269">Yes</span></span>|<span data-ttu-id="fbd45-270">Geçerli işlemi iptal edin ve yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbd45-270">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="fbd45-271">Oturumdaki tüm önceki iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-271">Resend all previous messages in the session.</span></span> <span data-ttu-id="fbd45-272">Tüm iletilerin başarıyla gönderildiği ve oturum daha fazla ileti olmadığını gösterdiği bir işlem oluşturulduktan sonra, tüm giden oturum kanalları kapatılır, alma bağlamlarının tümü işlemle tamamlanır, gelen oturum kanalı kapatılır ve işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-272">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="fbd45-273">Oturumlar çok noktaya yayın yaparken, hatasız bir hata olmayan mesajlar daha önce olduğu gibi aynı hedefe gönderilir ve bir hatayla karşılaşan iletiler yedekleme hedeflerine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-273">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="fbd45-274">Two-Way</span><span class="sxs-lookup"><span data-stu-id="fbd45-274">Two-Way</span></span>||||<span data-ttu-id="fbd45-275">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-275">Yes</span></span>|<span data-ttu-id="fbd45-276">Bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-276">Send to a backup destination.</span></span>  <span data-ttu-id="fbd45-277">Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.</span><span class="sxs-lookup"><span data-stu-id="fbd45-277">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="fbd45-278">Two-Way</span><span class="sxs-lookup"><span data-stu-id="fbd45-278">Two-Way</span></span>|<span data-ttu-id="fbd45-279">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-279">✔️</span></span>|||<span data-ttu-id="fbd45-280">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-280">Yes</span></span>|<span data-ttu-id="fbd45-281">Kanaldaki tüm iletileri bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-281">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="fbd45-282">Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.</span><span class="sxs-lookup"><span data-stu-id="fbd45-282">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="fbd45-283">Two-Way</span><span class="sxs-lookup"><span data-stu-id="fbd45-283">Two-Way</span></span>||<span data-ttu-id="fbd45-284">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-284">✔️</span></span>||<span data-ttu-id="fbd45-285">No</span><span class="sxs-lookup"><span data-stu-id="fbd45-285">No</span></span>|<span data-ttu-id="fbd45-286">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-286">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="fbd45-287">Two-Way</span><span class="sxs-lookup"><span data-stu-id="fbd45-287">Two-Way</span></span>|<span data-ttu-id="fbd45-288">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-288">✔️</span></span>|<span data-ttu-id="fbd45-289">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-289">✔️</span></span>||<span data-ttu-id="fbd45-290">No</span><span class="sxs-lookup"><span data-stu-id="fbd45-290">No</span></span>|<span data-ttu-id="fbd45-291">Bir özel durum oluşturulur ve işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-291">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="fbd45-292">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-292">Duplex</span></span>||||<span data-ttu-id="fbd45-293">No</span><span class="sxs-lookup"><span data-stu-id="fbd45-293">No</span></span>|<span data-ttu-id="fbd45-294">Oturum olmayan çift yönlü iletişim şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="fbd45-294">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="fbd45-295">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="fbd45-295">Duplex</span></span>|<span data-ttu-id="fbd45-296">✔️</span><span class="sxs-lookup"><span data-stu-id="fbd45-296">✔️</span></span>|||<span data-ttu-id="fbd45-297">Yes</span><span class="sxs-lookup"><span data-stu-id="fbd45-297">Yes</span></span>|<span data-ttu-id="fbd45-298">Bir yedekleme hedefine gönderin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-298">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="fbd45-299">Hosting</span><span class="sxs-lookup"><span data-stu-id="fbd45-299">Hosting</span></span>

<span data-ttu-id="fbd45-300">Yönlendirme hizmeti bir WCF hizmeti olarak uygulandığından, bir uygulama içinde kendi kendine barındırılan veya IIS ya da WAS tarafından barındırılan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-300">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="fbd45-301">Bu barındırma ortamlarında sunulan otomatik başlatma ve yaşam döngüsü yönetim özelliklerinden yararlanmak için yönlendirme hizmetinin IIS, WAS veya bir Windows hizmet uygulamasında barındırılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-301">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="fbd45-302">Aşağıdaki örnek, bir uygulamada yönlendirme hizmetinin barındırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-302">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="fbd45-303">Yönlendirme hizmetini IIS veya WAS içinde barındırmak için bir hizmet dosyası (. svc) oluşturmanız ya da hizmetin yapılandırma tabanlı etkinleştirmesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-303">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="fbd45-304">Bir hizmet dosyası kullanırken, <xref:System.ServiceModel.Routing.RoutingService> hizmet parametresini kullanarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-304">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="fbd45-305">Aşağıdaki örnek, yönlendirme hizmetini IIS veya WAS ile barındırmak için kullanılabilecek örnek bir hizmet dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-305">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="fbd45-306">Yönlendirme hizmeti ve kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="fbd45-306">Routing Service and Impersonation</span></span>

<span data-ttu-id="fbd45-307">WCF yönlendirme hizmeti, hem gönderme hem de alma iletileri için kimliğe bürünme ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-307">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="fbd45-308">Kimliğe bürünme için tüm olağan Windows kısıtlamaları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-308">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="fbd45-309">Kendi hizmetinizi yazarken kimliğe bürünme özelliğini kullanmak üzere hizmet veya hesap izinleri ayarlamanız gerekiyorsa, yönlendirme hizmeti ile kimliğe bürünme özelliğini kullanmak için bu adımları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-309">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="fbd45-310">Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="fbd45-310">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="fbd45-311">Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET uyumluluk modundayken ASP.NET Kimliğe bürünme özelliğinin kullanımını veya kimliğe bürünmeye izin verecek şekilde yapılandırılmış Windows kimlik bilgilerinin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-311">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="fbd45-312">ASP.NET uyumluluk modu hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="fbd45-312">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="fbd45-313">WCF yönlendirme hizmeti temel kimlik doğrulamasıyla kimliğe bürünme özelliğini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="fbd45-313">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="fbd45-314">Yönlendirme hizmeti ile ASP.NET Kimliğe bürünme özelliğini kullanmak için hizmet barındırma ortamında ASP.NET uyumluluk modunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="fbd45-314">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="fbd45-315">Yönlendirme hizmeti zaten ASP.NET uyumluluk moduna izin vermek üzere işaretlendi ve kimliğe bürünme otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-315">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="fbd45-316">Kimliğe bürünme, ASP.NET tümleştirmesi 'nin yönlendirme hizmeti ile desteklenen tek kullanımı.</span><span class="sxs-lookup"><span data-stu-id="fbd45-316">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="fbd45-317">Windows kimlik bilgisi kimliğe bürünme özelliğini yönlendirme hizmeti ile birlikte kullanmak için hem kimlik bilgilerini hem de hizmeti yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbd45-317">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="fbd45-318">İstemci kimlik bilgileri nesnesi (, <xref:System.ServiceModel.Security.WindowsClientCredential> öğesinden çözümlenemeyen), <xref:System.ServiceModel.ChannelFactory> <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> kimliğe bürünmeye izin vermek için ayarlanması gereken bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fbd45-318">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="fbd45-319">Son olarak, hizmette olarak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ayarlanacak davranışı yapılandırmanız gerekir `ImpersonateCallerForAllOperations` `true` .</span><span class="sxs-lookup"><span data-stu-id="fbd45-319">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="fbd45-320">Yönlendirme hizmeti, kimliğe bürünme özelliği etkinken iletileri iletmek için istemciler oluşturulup oluşturulmayacağını belirlemek için bu bayrağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbd45-320">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd45-321">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbd45-321">See also</span></span>

- [<span data-ttu-id="fbd45-322">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="fbd45-322">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="fbd45-323">Sözleşmeleri Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="fbd45-323">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="fbd45-324">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="fbd45-324">Choosing a Filter</span></span>](choosing-a-filter.md)
