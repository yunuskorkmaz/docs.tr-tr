---
title: "Yönlendirme Tanıtımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0fe14f096ae0914235ea1d23b874f0aea906d9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="routing-introduction"></a><span data-ttu-id="b34b7-102">Yönlendirme Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="b34b7-102">Routing Introduction</span></span>
<span data-ttu-id="b34b7-103">Yönlendirme hizmeti, ileti içeriğine göre yönlendirme iletilerinin özelliğine sahip bir genel takılabilir SOAP aracı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="b34b7-104">Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelik Yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolar uygulamak olanak tanıyan karmaşık bir yönlendirme mantık oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b34b7-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="b34b7-105">Yönlendirme hizmeti, işleme hatası, birincil hedef uç noktasına gönderilirken bir hata oluşursa, iletileri gönderildiği yedekleme uç noktaları listelerini ayarlamanıza olanak tanır de sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="b34b7-106">Bu konu için yönlendirme hizmeti yeni yöneliktir ve temel yapılandırma ve yönlendirme hizmeti barındırma kapsar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b34b7-107">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b34b7-107">Configuration</span></span>  
 <span data-ttu-id="b34b7-108">Yönlendirme hizmeti, istemci uygulamalarından iletileri almasına ve iletileri bir veya daha fazla hedef Uç noktalara yönlendirmek bir veya daha fazla hizmet uç noktaları kullanıma sunan bir WCF hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="b34b7-109">Hizmeti sağlayan bir <xref:System.ServiceModel.Routing.RoutingBehavior>, hizmet tarafından kullanıma sunulan hizmet uç noktalarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="b34b7-110">Bu davranış, hizmetin nasıl çalıştığı hakkında çeşitli yönlerini yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="b34b7-111">Üzerinde belirtilen bir yapılandırma dosyası kullanırken yapılandırma kolaylığı için parametreleri **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="b34b7-112">Kod tabanlı senaryolarda, bu parametreler parçası olarak belirtilen bir <xref:System.ServiceModel.Routing.RoutingConfiguration> için geçirilebilir nesnesi bir **RoutingBehavior**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="b34b7-113">Başlatma sırasında bu davranış ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, istemci uç noktaları için iletileri SOAP işlemeyi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="b34b7-114">Farklı bir Gerektirdiğiniz iletileri iletmek yönlendirme hizmeti böylece **MessageVersion** üzerinden alınan ileti uç nokta değerinden.</span><span class="sxs-lookup"><span data-stu-id="b34b7-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="b34b7-115">**RoutingBehavior** de bir hizmeti uzantı kayıtları <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için erişilebilirlik noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="b34b7-116">**RoutingConfiguration** sınıfı, yapılandırma ve yönlendirme hizmeti yapılandırmasını güncelleştirmek için tutarlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="b34b7-117">Yönlendirme hizmeti ayarlarını olarak davranmasına ve yapılandırmak için kullanılan parametreleri içeren **RoutingBehavior** hizmeti başladığında veya geçirilir **RoutingExtension** yönlendirme değiştirmek için Çalışma zamanında yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="b34b7-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="b34b7-118">İçerik tabanlı yönlendirme iletilerinin gerçekleştirmek için kullanılan yönlendirme mantığı birden çok gruplandırma tarafından tanımlanan <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri içine birlikte filtre tabloları (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneleri).</span><span class="sxs-lookup"><span data-stu-id="b34b7-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="b34b7-119">Gelen İleti Filtresi tablosu ve her ileti filtreleri karşı değerlendirilir **MessageFilter** hedef uç noktasına iletilen iletinin eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="b34b7-120">Kullanarak iletileri yönlendirmek için kullanılan filtre tablosunda belirtilen **RoutingBehavior** yapılandırmasında veya kullanarak kod aracılığıyla **RoutingConfiguration** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="b34b7-121">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="b34b7-121">Defining Endpoints</span></span>  
 <span data-ttu-id="b34b7-122">Kullanacağınız yönlendirme mantığı tanımlayarak yapılandırmanızı başlaması gerektiğini görünebilir, ancak ilk adımınız yönlendirme mesajlarına olacaktır uç noktaları şeklini belirlemek için gerçekten olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="b34b7-123">Yönlendirme hizmeti almak ve iletileri göndermek için kullanılan kanalları şekil tanımlamak sözleşmeleri kullanır ve bu nedenle Giriş kanalı şekli çıktı kanalı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="b34b7-124">İstek-yanıt kanal şekli kullanan uç noktaları yönlendirme, örneğin, sonra uyumlu bir sözleşme gelen uç noktalarda gibi kullanmalısınız <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="b34b7-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="b34b7-125">Başka bir deyişle, hedef uç noktaları (örneğin, tek yönlü ve iki yönlü işlemleri karıştırma) birden çok iletişim desenlerle sözleşmeleri kullanırsanız, alabilen ve bunların tümüne iletileri yönlendirmek tek hizmet uç noktası oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="b34b7-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="b34b7-126">Hangi uç noktaları uyumlu şekiller varsa ve hedef Uç noktalara yönlendirilmesi için iletileri almak için kullanılan bir veya daha fazla hizmet uç noktaları tanımlamak belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b34b7-127">Birden çok iletişim düzenleri (örneğin, tek yönlü ve iki yönlü işlemleri karışımını) belirtin sözleşmeleri ile çalışırken, geçici bir çözüm çift yönlü sözleşme yönlendirme hizmeti gibi kullanmaktır <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span><span class="sxs-lookup"><span data-stu-id="b34b7-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="b34b7-128">Ancak bu bağlama için tüm senaryoları mümkün olmayabilir çift yönlü iletişim yeteneğine sahip olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="b34b7-129">Bu mümkün olduğu senaryolarda, birden çok uç nokta içine iletişime Finansman veya uygulamayı değiştirirken gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="b34b7-130">Sözleşmeleri yönlendirme hakkında daha fazla bilgi için bkz: [sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b34b7-130">For more information about routing contracts, see [Routing Contracts](../../../../docs/framework/wcf/feature-details/routing-contracts.md).</span></span>  
  
 <span data-ttu-id="b34b7-131">Hizmet uç noktası tanımlandıktan sonra kullanabileceğiniz **RoutingBehavior** belirli bir ilişkilendirilecek **RoutingConfiguration** uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="b34b7-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="b34b7-132">Yönlendirme hizmeti bir yapılandırma dosyası kullanarak yapılandırırken **RoutingBehavior** Bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığını içerir Filtresi tablosu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="b34b7-133">Yönlendirme hizmeti program aracılığıyla yapılandırıyorsanız kullanarak filtreleme tablosu belirtebilirsiniz **RoutingConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="b34b7-134">Aşağıdaki örnek, programlı ve bir yapılandırma dosyası kullanarak yönlendirme hizmeti tarafından kullanılan hizmet ve istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b34b7-135">Bu örnekte "8000/routingservice/yönlendirilecek iletileri almak için kullanılan yönlendiricinin" adresi olan tek bir uç noktası kullanıma sunmak için yönlendirme hizmeti yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-135">This example configures the Routing Service to expose a single endpoint with an address of "http://localhost:8000/routingservice/router", which is used to receive messages to be routed.</span></span> <span data-ttu-id="b34b7-136">Hizmet uç noktası kullanır, iletiler istek-yanıt Uç noktalara yönlendirilir çünkü <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşme.</span><span class="sxs-lookup"><span data-stu-id="b34b7-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="b34b7-137">Bu yapılandırma ayrıca bir tek istemci uç noktası "8000/servicemodelsample/iletileri yönlendirilir hizmetinin" tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-137">This configuration also defines a single client endpoint of "http://localhost:8000/servicemodelsample/service" that messages are routed to.</span></span> <span data-ttu-id="b34b7-138">"RoutingTable1" adlı (gösterilmez) filtre tablo iletileri yönlendirmek için kullanılan yönlendirme mantığı içerir ve kullanarak hizmet uç noktası ile ilişkili **RoutingBehavior** (için bir yapılandırma dosyası) veya  **RoutingConfiguration** (için program yapılandırması).</span><span class="sxs-lookup"><span data-stu-id="b34b7-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="b34b7-139">Yönlendirme mantığı</span><span class="sxs-lookup"><span data-stu-id="b34b7-139">Routing Logic</span></span>  
 <span data-ttu-id="b34b7-140">İletileri yönlendirmek için kullanılan yönlendirme mantığını tanımlamak için ne gelen iletileri içinde bulunan verileri olabilir belirlemeniz gerekir benzersiz olarak sayısı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="b34b7-141">İyi bir gösterge aynı SOAP Eylemler, iletinin içinde yer alan eylem değerini paylaşmak için yönlendirme tüm hedef uç noktaları değilse, örneğin, belirli hangi uç noktasını ileti için yönlendirileceğini.</span><span class="sxs-lookup"><span data-stu-id="b34b7-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="b34b7-142">Benzersiz olarak belirli bir uç noktasına iletileri yönlendirmek gerekir varsa, ileti yönlendirilir hedef uç nokta benzersiz olarak tanımlayan veri üzerine filtre.</span><span class="sxs-lookup"><span data-stu-id="b34b7-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="b34b7-143">Yönlendirme hizmeti birkaç sağlar **MessageFilter** adres, eylem, uç nokta adı veya hatta bir XPath sorgusu gibi bir iletinin içinde belirli değerleri inceleyin uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="b34b7-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="b34b7-144">Bu uygulamalar hiçbiri gereksinimlerinizi karşılıyorsa, özel bir oluşturabilirsiniz **MessageFilter** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b34b7-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="b34b7-145">İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaları karşılaştırması hakkında daha fazla bilgi için bkz: [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md) ve [filtre seçme](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).</span><span class="sxs-lookup"><span data-stu-id="b34b7-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md) and [Choosing a Filter](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="b34b7-146">Birden çok ileti filtreleri birlikte her ilişkilendirmek filtre tablolara düzenlenir **MessageFilter** hedef uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="b34b7-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="b34b7-147">İsteğe bağlı olarak, filtre tablosunda yönlendirme hizmeti için bir iletim hatası durumunda iletiyi göndermeyi deneyecek yedekleme bitiş noktaları listesini belirtmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="b34b7-148">Varsayılan olarak tüm ileti filtreleri Filtresi tablosu içinde eşzamanlı olarak değerlendirilir; Ancak, belirleyebileceğiniz bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> belirli bir sırada değerlendirilecek ileti filtreleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="b34b7-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="b34b7-149">En yüksek önceliğe sahip tüm girişleri ilk olarak değerlendirilir ve daha yüksek bir öncelik düzeyde bir eşleşme bulunamazsa, ileti filtreleri alt öncelikler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="b34b7-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="b34b7-150">Filtre tabloları hakkında daha fazla bilgi için bkz: [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="b34b7-150">For more information about filter tables, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="b34b7-151">Aşağıdaki örneklerde <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, hesaplar için `true` tüm iletiler için.</span><span class="sxs-lookup"><span data-stu-id="b34b7-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="b34b7-152">Bu **MessageFilter** ilişkilendiren "routingTable1" filtre tabloya eklenen **MessageFilter** "CalculatorService" adlı istemci uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="b34b7-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="b34b7-153">**RoutingBehavior** Bu tablo Hizmeti uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
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
>  <span data-ttu-id="b34b7-154">Varsayılan olarak, yönlendirme hizmeti, yalnızca ileti üstbilgilerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="b34b7-155">İleti gövdesi erişmek için filtreleri izin vermek için ayarlamanız gerekir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="b34b7-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="b34b7-156">**Çok noktaya yayın**</span><span class="sxs-lookup"><span data-stu-id="b34b7-156">**Multicast**</span></span>  
  
 <span data-ttu-id="b34b7-157">Birçok yönlendirme hizmeti yapılandırması yalnızca bir özel uç noktasına iletileri yönlendiren özel filtre mantığı kullanırken, belirli bir ileti birden çok hedef Uç noktalara yönlendirmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="b34b7-158">Çok noktaya yayın ileti birden çok varış yeri için aşağıdaki koşulların doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b34b7-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
-   <span data-ttu-id="b34b7-159">Kanal şekli istek-yanıt olmamalıdır (ancak tek yönlü veya çift yönlü olabilir) çünkü isteğine yanıt olarak istemci uygulaması tarafından yalnızca bir yanıt aldı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
-   <span data-ttu-id="b34b7-160">Birden çok filtre döndürmelidir `true` ileti değerlendirirken.</span><span class="sxs-lookup"><span data-stu-id="b34b7-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="b34b7-161">Bu koşullar karşılanıyorsa, ileti tüm uç noktaları için değerlendirin tüm filtreleri yönlendirilir `true`.</span><span class="sxs-lookup"><span data-stu-id="b34b7-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="b34b7-162">Aşağıdaki örnek, uç nokta adresi iletisi 8000/routingservice/yönlendirici/yuvarlama ise her iki uç noktalara yönlendirilen iletilerinde sonuçları bir yönlendirme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is http://localhost:8000/routingservice/router/rounding.</span></span>  
  
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
  
### <a name="soap-processing"></a><span data-ttu-id="b34b7-163">SOAP işleme</span><span class="sxs-lookup"><span data-stu-id="b34b7-163">SOAP Processing</span></span>  
 <span data-ttu-id="b34b7-164">İletileri farklı protokoller arasında yönlendirme desteklemek için **RoutingBehavior** varsayılan ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletileri yönlendirilir tüm istemci uç için.</span><span class="sxs-lookup"><span data-stu-id="b34b7-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="b34b7-165">Bu davranış otomatik olarak yeni bir oluşturur **MessageVersion** uyumlu bir oluşturma yanı sıra uç noktasına ileti yönlendirme önce **MessageVersion** kendisine dönmeden önce herhangi bir yanıt belge için istekte bulunan istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="b34b7-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="b34b7-166">Yeni bir oluşturmak için adımlar **MessageVersion** giden ileti için aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b34b7-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="b34b7-167">**İstek işleme**</span><span class="sxs-lookup"><span data-stu-id="b34b7-167">**Request processing**</span></span>  
  
-   <span data-ttu-id="b34b7-168">Alma **MessageVersion** kanalının giden bağlama /.</span><span class="sxs-lookup"><span data-stu-id="b34b7-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
-   <span data-ttu-id="b34b7-169">Gövde Okuyucu için özgün iletisini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b34b7-169">Get the body reader for the original message.</span></span>  
  
-   <span data-ttu-id="b34b7-170">Aynı eylemi, gövde okuyucu ve yeni bir ile yeni bir ileti oluşturma **MessageVersion**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
-   <span data-ttu-id="b34b7-171">Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, Kopyala ve yeni iletisi RelatesTo üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="b34b7-172">Tüm ileti özellikleri yeni bir iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-172">Copy all message properties to the new message.</span></span>  
  
-   <span data-ttu-id="b34b7-173">Yanıtı işlerken kullanılacak özgün istek iletisi depolar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-173">Store the original request message to use when processing the response.</span></span>  
  
-   <span data-ttu-id="b34b7-174">Yeni İstek iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="b34b7-175">**Yanıt işleme**</span><span class="sxs-lookup"><span data-stu-id="b34b7-175">**Response processing**</span></span>  
  
-   <span data-ttu-id="b34b7-176">Alma **MessageVersion** özgün istek iletisi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-176">Get the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="b34b7-177">Gövde Okuyucu için alınan yanıt iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-177">Get the body reader for the received response message.</span></span>  
  
-   <span data-ttu-id="b34b7-178">Gövde okuyucu aynı eylemi yeni bir yanıt iletisi oluşturmak ve **MessageVersion** özgün istek iletisi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
-   <span data-ttu-id="b34b7-179">Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, Kopyala ve yeni iletisi RelatesTo üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
-   <span data-ttu-id="b34b7-180">İleti özellikleri yeni bir iletiye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-180">Copy the message properties to the new message.</span></span>  
  
-   <span data-ttu-id="b34b7-181">Yeni yanıt iletisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="b34b7-182">Varsayılan olarak, **SoapProcessingBehavior** istemci uç noktaları tarafından otomatik olarak eklenir <xref:System.ServiceModel.Routing.RoutingBehavior> hizmeti başladığında; ancak, kullanarak SOAP işleme için tüm istemci uç noktaları eklenip eklenmediğini kontrol edebilirsiniz <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b34b7-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="b34b7-183">Ayrıca davranışı doğrudan belirli bir bitiş noktasına eklemek ve da etkinleştirebilir veya SOAP işleme konusunda daha ayrıntılı bir denetim gerekli olduğunda bu davranış uç nokta düzeyinde devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b34b7-184">SOAP işleme özgün istek iletisi daha farklı MessageVersion gerektiren bir uç nokta için devre dışı bırakılırsa, iletiyi göndermeden önce gerekli herhangi bir SOAP değişiklik gerçekleştirmek için özel bir mekanizma sağlamanız gerekir Hedef uç noktası.</span><span class="sxs-lookup"><span data-stu-id="b34b7-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="b34b7-185">Aşağıdaki örneklerde, **soapProcessingEnabled** önlemek için kullanılan özellik **SoapProcessingBehavior** için tüm istemci uç noktalarını otomatik olarak eklenmesini.</span><span class="sxs-lookup"><span data-stu-id="b34b7-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
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
  
### <a name="dynamic-configuration"></a><span data-ttu-id="b34b7-186">Dinamik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b34b7-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="b34b7-187">Ek istemci uç noktalarını eklemek veya iletileri yönlendirmek için kullanılan filtreleri değiştirmek için ihtiyacınız olduğunda hizmet şu anda üzerinden ileti alma Uç noktalara kesilmesini önlemek için dinamik olarak çalışma zamanında yapılandırmasını güncelleştirmek için bir yol olması gerekir Yönlendirme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="b34b7-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="b34b7-188">Her iki yöntem hiçbir ileti şu anda transit ve olası olası kaybı için kapalı kalma süresi sırasında için sunulmasını uygulamasını geri dönüşüme gerektirdiğinden bir yapılandırma dosyası veya konak uygulama kodunu değiştirme her zaman yeterli değil hizmetin yeniden başlatılması bekliyor.</span><span class="sxs-lookup"><span data-stu-id="b34b7-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="b34b7-189">Yalnızca değiştirebileceğiniz **RoutingConfiguration** programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="b34b7-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="b34b7-190">Hizmet yapılandırma dosyası kullanarak başlangıçta yapılandırabilirsiniz ancak, yalnızca çalışma zamanında yapılandırma yeni bir oluşturarak değiştirebilirsiniz **RoutingConfigution** ve parametre olarak geçirme <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yöntemi tarafından sunulan <xref:System.ServiceModel.Routing.RoutingExtension> hizmet uzantısı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfigution** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="b34b7-191">Çağrısından sonra alınan iletilerin çalışırken önceki yapılandırmayı kullanarak yönlendirilecek şu anda yoldaki tüm iletileri devam **ApplyConfiguration** yeni yapılandırmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="b34b7-192">Aşağıdaki örnek, yönlendirme hizmeti örneği oluşturmayı ve daha sonra yapılandırmasını değiştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
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
>  <span data-ttu-id="b34b7-193">Bu şekilde yönlendirme hizmeti güncelleştirirken yalnızca yeni bir yapılandırma geçişi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="b34b7-194">Geçerli yapılandırma yalnızca seçilen öğeleri değiştirmek veya geçerli yapılandırması için yeni girdileri eklemek mümkün değildir; oluşturmanız ve varolan yerini yeni bir yapılandırma geçişi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b34b7-195">Önceki yapılandırmayı kullanarak açılan oturumlar önceki yapılandırmayı kullanarak devam edin.</span><span class="sxs-lookup"><span data-stu-id="b34b7-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="b34b7-196">Yeni yapılandırma, yalnızca yeni oturumlar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="b34b7-197">Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="b34b7-197">Error Handling</span></span>  
 <span data-ttu-id="b34b7-198">Varsa <xref:System.ServiceModel.CommunicationException> hata meydana işleme bir ileti göndermeye çalışırken hatayla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="b34b7-199">Bu özel durumlar gibi tanımlanmış istemci uç noktası ile iletişim kurmaya çalışırken bir sorunla karşılaşıldı genellikle belirtmek bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="b34b7-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="b34b7-200">Hata işleme kodu da yakalamak ve ne zaman göndermeyi yeniden deneme girişimi bir <xref:System.TimeoutException> oluşur, türetilmedi başka bir ortak özel durumu olan **CommunicationException**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="b34b7-201">Önceki özel durumlardan birini ortaya çıktığında, yönlendirme hizmeti üzerinden bir yedekleme uç noktaları listesine başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b34b7-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="b34b7-202">Tüm yedekleme uç noktaları bir iletişim hatası ile başarısız ya da bir uç nokta bir özel durum döndürürse hedef hizmetinde bir hata gösterir, yönlendirme hizmeti istemci uygulamasına bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b34b7-203">Hata işleme işlevselliği yakalar ve bir ileti göndermeye çalışırken ve kanal kapatılmaya çalışılırken oluşan özel durumları işler.</span><span class="sxs-lookup"><span data-stu-id="b34b7-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="b34b7-204">Hata işleme kodu algılamak veya ile iletişim uygulama uç noktaları tarafından oluşturulan özel durumları işlemek üzere tasarlanmamıştır; bir <xref:System.ServiceModel.FaultException> tarafından oluşturulan bir hizmet yönlendirme hizmeti görünür bir **FaultMessage** ve istemciye akıtılan.</span><span class="sxs-lookup"><span data-stu-id="b34b7-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="b34b7-205">Yönlendirme hizmeti bir ileti geçiş yapmaya çalıştığında bir hata oluşursa, alabilirsiniz bir <xref:System.ServiceModel.FaultException> istemci tarafında yerine bir <xref:System.ServiceModel.EndpointNotFoundException> normalde yönlendirme hizmeti olmaması durumunda alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b34b7-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="b34b7-206">Yönlendirme hizmeti, böylece özel durumlar maske ve iç içe geçmiş özel durumları inceleyin sürece tam saydamlığı sağlamak için değil olabilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="b34b7-207">Özel durum izleme</span><span class="sxs-lookup"><span data-stu-id="b34b7-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="b34b7-208">Bir listedeki bir uç nokta ileti başarısız gönderirken, yönlendirme hizmeti ortaya çıkan özel durum verileri izler ve özel durum ayrıntıları adlı bir ileti özelliği ekler **özel durumları**.</span><span class="sxs-lookup"><span data-stu-id="b34b7-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="b34b7-209">Bu özel durum verileri korur ve ileti denetçisi aracılığıyla kullanıcı programlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="b34b7-210">Özel durum verileri, her ileti bir ileti göndermeye çalışırken karşılaşılan özel durum ayrıntıları uç nokta adı eşlendiği sözlükte depolanır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="b34b7-211">Yedekleme uç noktaları</span><span class="sxs-lookup"><span data-stu-id="b34b7-211">Backup Endpoints</span></span>  
 <span data-ttu-id="b34b7-212">Filtre tablo içindeki her filtre giriş isteğe bağlı olarak bir iletim hatası durumunda birincil uç noktasına gönderirken kullanılan yedekleme bitiş noktaları listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b34b7-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="b34b7-213">Bu tür bir hata oluşursa, yönlendirme hizmeti yedekleme endpoint listedeki ilk giriş iletiyi iletme dener.</span><span class="sxs-lookup"><span data-stu-id="b34b7-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="b34b7-214">Bu gönderme girişimi de iletim hatasının karşılaşırsa, yedek listeyi sonraki uç denenir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="b34b7-215">Yönlendirme hizmeti iletiyi başarıyla alınırsa, tüm uç noktaları iletim hata döndürür veya bir olmayan iletim hatasının bir uç noktası tarafından döndürülen kadar listesindeki her bir uç nokta için ileti gönderilirken devam eder.</span><span class="sxs-lookup"><span data-stu-id="b34b7-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="b34b7-216">Aşağıdaki örnekler bir yedekleme listesi kullanmak için yönlendirme hizmeti yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
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
  
### <a name="supported-error-patterns"></a><span data-ttu-id="b34b7-217">Desteklenen hata desenleri</span><span class="sxs-lookup"><span data-stu-id="b34b7-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="b34b7-218">Aşağıdaki tabloda, yedekleme endpoint listeleri, hata işleme için belirli desenleri ayrıntılarını açıklayan Notlar birlikte kullanımı ile uyumlu desenleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b34b7-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="b34b7-219">Desen</span><span class="sxs-lookup"><span data-stu-id="b34b7-219">Pattern</span></span>|<span data-ttu-id="b34b7-220">Oturum</span><span class="sxs-lookup"><span data-stu-id="b34b7-220">Session</span></span>|<span data-ttu-id="b34b7-221">İşlem</span><span class="sxs-lookup"><span data-stu-id="b34b7-221">Transaction</span></span>|<span data-ttu-id="b34b7-222">Bağlamı alma</span><span class="sxs-lookup"><span data-stu-id="b34b7-222">Receive Context</span></span>|<span data-ttu-id="b34b7-223">Desteklenen yedekleme listesi</span><span class="sxs-lookup"><span data-stu-id="b34b7-223">Backup List Supported</span></span>|<span data-ttu-id="b34b7-224">Notlar</span><span class="sxs-lookup"><span data-stu-id="b34b7-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="b34b7-225">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-225">One-Way</span></span>||||<span data-ttu-id="b34b7-226">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-226">Yes</span></span>|<span data-ttu-id="b34b7-227">Yedek bir uç noktada iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="b34b7-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="b34b7-228">Bu ileti yaşanıyorsa çok noktaya yayın, yalnızca ileti başarısız kanalda yedekleme hedefine taşındı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="b34b7-229">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-229">One-Way</span></span>||<span data-ttu-id="b34b7-230">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-230">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="b34b7-231">Hayır</span><span class="sxs-lookup"><span data-stu-id="b34b7-231">No</span></span>|<span data-ttu-id="b34b7-232">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="b34b7-233">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-233">One-Way</span></span>|||<span data-ttu-id="b34b7-234">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-234">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-235">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-235">Yes</span></span>|<span data-ttu-id="b34b7-236">Yedek bir uç noktada iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="b34b7-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="b34b7-237">İleti sonra başarıyla alındı, tam tüm bağlamları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b34b7-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="b34b7-238">İleti tarafından herhangi bir uç nokta başarıyla alınmazsa alma bağlamı tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="b34b7-239">Bu ileti yükleniyor zaman çok noktaya yayın alma bağlamı ileti en az bir uç noktası tarafından (birincil veya yedek) başarıyla alınırsa yalnızca tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="b34b7-240">Uç noktalarını çok noktaya yayın yolların hiçbiri başarılı bir şekilde iletisi alırsanız, alma bağlamı tamamlamayın.</span><span class="sxs-lookup"><span data-stu-id="b34b7-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="b34b7-241">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-241">One-Way</span></span>||<span data-ttu-id="b34b7-242">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-242">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-243">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-243">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-244">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-244">Yes</span></span>|<span data-ttu-id="b34b7-245">Önceki işlem abort, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="b34b7-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="b34b7-246">Bir hata ile karşılaştı iletileri bir yedekleme hedefine iletilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="b34b7-247">Bir işlem oluşturulduktan sonra tüm iletimler başarısız, alma bağlamları tamamlayın ve hareketi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="b34b7-248">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-248">One-Way</span></span>|<span data-ttu-id="b34b7-249">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-249">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="b34b7-250">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-250">Yes</span></span>|<span data-ttu-id="b34b7-251">Yedek bir uç noktada iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="b34b7-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="b34b7-252">Çok noktaya yayın senaryoda yalnızca iletileri bir hatayla karşılaştı bir oturumda veya oturumunda başarısız oturumunu kapatmak için yedekleme hedefi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="b34b7-253">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-253">One-Way</span></span>|<span data-ttu-id="b34b7-254">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-254">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-255">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-255">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="b34b7-256">Hayır</span><span class="sxs-lookup"><span data-stu-id="b34b7-256">No</span></span>|<span data-ttu-id="b34b7-257">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="b34b7-258">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-258">One-Way</span></span>|<span data-ttu-id="b34b7-259">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-259">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="b34b7-260">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-260">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-261">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-261">Yes</span></span>|<span data-ttu-id="b34b7-262">Yedek bir uç noktada iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="b34b7-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="b34b7-263">Tüm hata tamamlandı iletisi sonra oturumu başka iletilerin gösterir ve yönlendirme hizmeti başarıyla tüm giden oturum kanal kapatır, alması bağlamları tamamlanır ve gelen oturum kanalı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="b34b7-264">Tek Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-264">One-Way</span></span>|<span data-ttu-id="b34b7-265">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-265">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-266">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-266">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-267">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-267">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-268">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-268">Yes</span></span>|<span data-ttu-id="b34b7-269">Geçerli işlem iptal etmek ve yeni bir tane oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b34b7-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="b34b7-270">Tüm önceki iletileri oturumu yeniden gönderin.</span><span class="sxs-lookup"><span data-stu-id="b34b7-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="b34b7-271">Bir işlem, tüm iletileri başarıyla gönderildi oluşturulduktan sonra daha fazla ileti, tüm giden oturum kanalları kapalı olduğundan, alma oturumu gösterir bağlamları tüm işlemle tamamlanır, gelen oturum kanalı Kapalı, ve işlem taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="b34b7-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="b34b7-272">Çok noktaya yayın aynı hedefe önce herhangi bir hata vardı iletileri gönderilir ve bir hata ile karşılaştı iletileri oturumları zaman olan yedekleme hedefi için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="b34b7-273">Çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-273">Two-Way</span></span>||||<span data-ttu-id="b34b7-274">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-274">Yes</span></span>|<span data-ttu-id="b34b7-275">Bir yedekleme hedefine Gönder.</span><span class="sxs-lookup"><span data-stu-id="b34b7-275">Send to a backup destination.</span></span>  <span data-ttu-id="b34b7-276">Bir kanal bir yanıt iletisi döndüren sonra özgün istemci yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="b34b7-277">Çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-277">Two-Way</span></span>|<span data-ttu-id="b34b7-278">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-278">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="b34b7-279">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-279">Yes</span></span>|<span data-ttu-id="b34b7-280">Tüm iletileri kanalda bir yedekleme hedefine Gönder.</span><span class="sxs-lookup"><span data-stu-id="b34b7-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="b34b7-281">Bir kanal bir yanıt iletisi döndüren sonra özgün istemci yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b34b7-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="b34b7-282">Çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-282">Two-Way</span></span>||<span data-ttu-id="b34b7-283">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-283">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="b34b7-284">Hayır</span><span class="sxs-lookup"><span data-stu-id="b34b7-284">No</span></span>|<span data-ttu-id="b34b7-285">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="b34b7-286">Çift yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-286">Two-Way</span></span>|<span data-ttu-id="b34b7-287">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-287">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|<span data-ttu-id="b34b7-288">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-288">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>||<span data-ttu-id="b34b7-289">Hayır</span><span class="sxs-lookup"><span data-stu-id="b34b7-289">No</span></span>|<span data-ttu-id="b34b7-290">Bir özel durum ve işlem geri alındı.</span><span class="sxs-lookup"><span data-stu-id="b34b7-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="b34b7-291">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-291">Duplex</span></span>||||<span data-ttu-id="b34b7-292">Hayır</span><span class="sxs-lookup"><span data-stu-id="b34b7-292">No</span></span>|<span data-ttu-id="b34b7-293">Çift yönlü iletişimi olmayan oturumu şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b34b7-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="b34b7-294">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="b34b7-294">Duplex</span></span>|<span data-ttu-id="b34b7-295">![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")</span><span class="sxs-lookup"><span data-stu-id="b34b7-295">![Check mark](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")</span></span>|||<span data-ttu-id="b34b7-296">Evet</span><span class="sxs-lookup"><span data-stu-id="b34b7-296">Yes</span></span>|<span data-ttu-id="b34b7-297">Bir yedekleme hedefine Gönder.</span><span class="sxs-lookup"><span data-stu-id="b34b7-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="b34b7-298">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b34b7-298">Hosting</span></span>  
 <span data-ttu-id="b34b7-299">Yönlendirme hizmeti bir WCF hizmeti olarak uygulanması için ya da bir uygulama içinde kendi kendini barındıran veya gerekir barındırılan IIS ya da WAS tarafından.</span><span class="sxs-lookup"><span data-stu-id="b34b7-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="b34b7-300">Yönlendirme hizmeti, IIS, WAS veya bir Windows hizmet uygulaması otomatik olarak başlamasını yararlanabilir ve yaşam döngüsü yönetimi özellikleri bu barındırma ortamlarında kullanılabilir barındırılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="b34b7-301">Aşağıdaki örnek, yönlendirme hizmeti bir uygulamada barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="b34b7-302">Yönlendirme hizmeti IIS ya da WAS içinde barındırmak için bir hizmet dosyası (.svc) oluşturmanız veya yapılandırma temelli etkinleştirme hizmetinin kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="b34b7-303">Bir hizmeti dosyasını kullanırken belirtmelisiniz <xref:System.ServiceModel.Routing.RoutingService> hizmet parametresini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b34b7-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="b34b7-304">Aşağıdaki örnek, yönlendirme hizmeti IIS ya da WAS ile barındırmak için kullanılan bir örnek hizmet dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="b34b7-305">Yönlendirme hizmeti ile kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="b34b7-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="b34b7-306">WCF yönlendirme hizmeti ile kimliğe bürünme hem ileti gönderme ve alma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="b34b7-307">Tüm kimliğe bürünme normal Windows kısıtlamalar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="b34b7-308">Kimliğe bürünme kendi hizmet yazarken kullanmak için hizmet veya hesap izinlerini ayarlamak gerekli, kimliğe bürünme yönlendirme hizmeti ile kullanmak için bu aynı adımları gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="b34b7-309">Daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="b34b7-309">For more information, see [Delegation and Impersonation](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="b34b7-310">Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET kimliğe bürünme ASP.NET uyumluluğu modundayken kullanımını ya da kimliğe bürünme izin verecek şekilde yapılandırılmış Windows kimlik bilgilerinin kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="b34b7-311">ASP.NET uyumluluğu modu hakkında daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="b34b7-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b34b7-312">Yönlendirme WCF Hizmeti temel kimlik doğrulaması ile kimliğe bürünme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b34b7-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="b34b7-313">ASP.NET kimliğe bürünme yönlendirme hizmeti ile kullanmak için barındırma ortamı Service ASP.NET uyumluluğu modunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b34b7-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="b34b7-314">Yönlendirme hizmeti zaten ASP.NET uyumluluk modu ve kimliğe bürünme özelliğini otomatik olarak etkinleştirilecek izin verme olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="b34b7-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="b34b7-315">Kimliğe bürünme ASP.NET tümleştirme yönlendirme hizmeti ile yalnızca desteklenen kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="b34b7-316">Windows kimlik bilgisi kimliğe bürünme yönlendirme hizmeti ile kullanmak için kimlik bilgileri ve hizmet yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="b34b7-317">İstemci kimlik bilgileri nesnesini (<xref:System.ServiceModel.Security.WindowsClientCredential>, gelen accessable <xref:System.ServiceModel.ChannelFactory>) tanımlayan bir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği kimliğe bürünme izin verecek şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b34b7-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="b34b7-318">Son olarak, hizmette yapılandırmanız gereken <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ayarlamak için davranış `ImpersonateCallerForAllOperations` için `true`.</span><span class="sxs-lookup"><span data-stu-id="b34b7-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="b34b7-319">Yönlendirme hizmeti ile kimliğe bürünme etkin iletilerini yönlendirmede istemcileri oluşturma karar vermek için bu bayrağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b34b7-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34b7-320">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b34b7-320">See Also</span></span>  
 [<span data-ttu-id="b34b7-321">İleti Filtreleri</span><span class="sxs-lookup"><span data-stu-id="b34b7-321">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="b34b7-322">Anlaşmaları Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b34b7-322">Routing Contracts</span></span>](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [<span data-ttu-id="b34b7-323">Filtre Seçme</span><span class="sxs-lookup"><span data-stu-id="b34b7-323">Choosing a Filter</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
