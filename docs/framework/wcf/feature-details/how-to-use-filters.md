---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: ''
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-filters"></a><span data-ttu-id="923c6-102">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="923c6-102">How To: Use Filters</span></span>
<span data-ttu-id="923c6-103">Bu konu, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlarda özetler.</span><span class="sxs-lookup"><span data-stu-id="923c6-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="923c6-104">Bu örnekte, iletiler için bir hesap makinesi hizmetinin, regularCalc ve roundingCalc iki uygulamaları yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="923c6-105">Her iki uygulamaları aynı işlemleri destekler; Ancak bir hizmet döndürmeden önce hesaplamalarının yakın tamsayı değere yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="923c6-106">Bir istemci uygulaması hizmetinin yuvarlama sürümü kullanılıp kullanılmayacağını belirtmek kurabilmesi gerekir; Hizmet tercih ifade, ileti iki hizmetleri arasında dengeli yoktur.</span><span class="sxs-lookup"><span data-stu-id="923c6-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="923c6-107">Her iki Hizmetleri tarafından sunulan işlemleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="923c6-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="923c6-108">Ekle</span><span class="sxs-lookup"><span data-stu-id="923c6-108">Add</span></span>  
  
-   <span data-ttu-id="923c6-109">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="923c6-109">Subtract</span></span>  
  
-   <span data-ttu-id="923c6-110">Çarp</span><span class="sxs-lookup"><span data-stu-id="923c6-110">Multiply</span></span>  
  
-   <span data-ttu-id="923c6-111">Bölme</span><span class="sxs-lookup"><span data-stu-id="923c6-111">Divide</span></span>  
  
 <span data-ttu-id="923c6-112">Her iki hizmet işlemlerin aynısını uyguladığınız için iletide belirtilen eylemi benzersiz olmayacağından, eylem filtresi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="923c6-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="923c6-113">Bunun yerine iletileri uygun Uç noktalara yönlendirildiğinden emin olmak için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="923c6-114">Benzersiz veri belirleme</span><span class="sxs-lookup"><span data-stu-id="923c6-114">Determine Unique Data</span></span>  
  
1.  <span data-ttu-id="923c6-115">Her iki hizmet uygulamaları aynı işlemleri işlemek ve dışında döndürmeleri veri temelde aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemenize izin vermek için benzersiz değil İstek.</span><span class="sxs-lookup"><span data-stu-id="923c6-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="923c6-116">Ancak daha sonra istemci uygulamasının iletiye benzersiz üstbilgi değeri eklerse, ileti nasıl yönlendirileceğini belirlemek için bu değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="923c6-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="923c6-117">İstemci uygulaması yuvarlama hesaplayıcı tarafından işlenmek üzere ileti gerekiyorsa bu örnek için onu bir özel üst bilgi aşağıdaki kodu kullanarak ekler:</span><span class="sxs-lookup"><span data-stu-id="923c6-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="923c6-118">Şimdi bu başlığı iletilerde incelemek için XPath filtresi kullanın ve roundCalc hizmetine üstbilgisini içeren iletileri yönlendirmek.</span><span class="sxs-lookup"><span data-stu-id="923c6-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2.  <span data-ttu-id="923c6-119">Yönlendirme hizmeti EndpointName, EndpointAddress, kullanılabilir iki sanal hizmet uç noktalarına ek olarak kullanıma sunar veya benzersiz olarak uç noktada dayalı belirli hesaplayıcı uygulamasına gelen iletileri yönlendirmek için PrefixEndpointAddress filtreleri için istemci uygulaması isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="923c6-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="923c6-120">Uç noktaları tanımlayın</span><span class="sxs-lookup"><span data-stu-id="923c6-120">Define Endpoints</span></span>  
  
1.  <span data-ttu-id="923c6-121">Yönlendirme hizmeti tarafından kullanılan uç noktalarını tanımlarken, istemciler ve hizmetler tarafından kullanılan kanal şeklini belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="923c6-122">Bu senaryoda, her iki hedef hizmet istek-yanıt düzeni kullanın. Bu nedenle <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="923c6-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="923c6-123">Aşağıdaki örnek yönlendirme hizmeti tarafından sunulan hizmet uç noktaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="923c6-124">Bu yapılandırma ile yönlendirme hizmeti üç ayrı uç noktalarını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="923c6-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="923c6-125">Çalışma zamanı seçenekler bağlı olarak, istemci uygulaması iletileri bu adresleri biri olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="923c6-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="923c6-126">("Yuvarlama/hesaplayıcı" veya "normal/hesaplayıcı") "sanal" hizmet uç noktalarına birini gelen iletiler için karşılık gelen hesaplayıcı uygulama iletilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="923c6-127">İstemci uygulaması için özel bir uç nokta isteği göndermez, ileti genel uç noktasına değinilmiştir.</span><span class="sxs-lookup"><span data-stu-id="923c6-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="923c6-128">Seçilen uç nokta bağımsız olarak, istemci uygulaması da ileti yuvarlama hesaplayıcı kullanımla iletilen olduğunu belirtmek için özel üstbilgisini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="923c6-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2.  <span data-ttu-id="923c6-129">Aşağıdaki örnek, yönlendirme hizmeti, iletileri yönlendirir (hedef) istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="923c6-130">Bu uç noktalar filtre tablosunda belirli bir filtre eşleştiğinde iletisi gönderilir hedef uç noktası belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="923c6-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="923c6-131">Filtrelerin tanımlayın</span><span class="sxs-lookup"><span data-stu-id="923c6-131">Define Filters</span></span>  
  
1.  <span data-ttu-id="923c6-132">İstemci uygulaması iletiye ekler "RoundingCalculator" özel üstbilgi göre iletileri yönlendirmek için bu üst varlığını denetlemek için bir XPath sorgusu kullanan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="923c6-133">Özel bir ad alanını kullanarak bu başlığı tanımlı olduğundan, ayrıca "kullanılan özel" bir özel ad alanı önekini XPath sorgusu tanımlayan bir ad alanı girişi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="923c6-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="923c6-134">Aşağıdaki örnek gerekli yönlendirme bölüm, ad alanı tablo ve XPath filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="923c6-135">Bu **MessageFilter** "yuvarlama" değeri içeren iletisini RoundingCalculator üstbilgisinde arar.</span><span class="sxs-lookup"><span data-stu-id="923c6-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="923c6-136">Bu üst ileti roundingCalc hizmete yönlendirileceğini belirtmek için istemci tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="923c6-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="923c6-137">S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve ad alanını temsil "http://www.w3.org/2003/05/soap-envelope".</span><span class="sxs-lookup"><span data-stu-id="923c6-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace "http://www.w3.org/2003/05/soap-envelope".</span></span>  
  
2.  <span data-ttu-id="923c6-138">Ayrıca iki sanal uç noktalarda alınan iletilerin Ara filtreleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="923c6-139">İlk sanal uç nokta "normal/hesaplayıcı" uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="923c6-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="923c6-140">İstemci, ileti regularCalc hizmete yönlendirileceğini belirtmek için bu uç noktaya istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="923c6-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="923c6-141">Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ileti filterData içinde belirtilen ada sahip bir uç noktası aracılığıyla ulaştığında, belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="923c6-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="923c6-142">Bir ileti "calculatorEndpoint" adlı hizmet uç noktası tarafından alınmazsa, bu filtresinin `true`.</span><span class="sxs-lookup"><span data-stu-id="923c6-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3.  <span data-ttu-id="923c6-143">Ardından, roundingEndpoint adresine gönderilen iletileri arar bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="923c6-144">İstemci, ileti roundingCalc hizmete yönlendirileceğini belirtmek için bu uç noktaya istekleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="923c6-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="923c6-145">Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ileti "yuvarlama/hesaplayıcı" uç noktada ulaştığında, belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="923c6-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="923c6-146">"http://localhost/routingservice/router/rounding/" ile başlayan adreste bir ileti alındığında sonra bu filtresinin **doğru**.</span><span class="sxs-lookup"><span data-stu-id="923c6-146">If a message is received at an address that begins with "http://localhost/routingservice/router/rounding/" then this filter evaluates to **true**.</span></span> <span data-ttu-id="923c6-147">Bu yapılandırma tarafından kullanılan temel adres "http://localhost/routingservice/router" ve roundingEndpoint için belirtilen adresi "yuvarlama/hesaplayıcı" olduğundan bu bitiş noktası ile iletişim kurmak için kullanılan tam "http://localhost/routingservice/router/rounding/calculator" adresidir Bu filtre ile eşleşen hesaplayıcı.</span><span class="sxs-lookup"><span data-stu-id="923c6-147">Because the base address used by this configuration is "http://localhost/routingservice/router" and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is "http://localhost/routingservice/router/rounding/calculator", which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="923c6-148">PrefixEndpointAddress filtre ana bilgisayar adı, tek bir ana bilgisayar için tüm olabilir ana bilgisayar adlarını çeşitli kullanarak başvurulabilir olduğundan bir eşleşme gerçekleştirme konağa istemci uygulamasından başvuran geçerli yolu kullanırken değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="923c6-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="923c6-149">Örneğin, aşağıdakilerin tümü aynı ana bilgisayarına başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="923c6-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    >  -   <span data-ttu-id="923c6-150">localhost</span><span class="sxs-lookup"><span data-stu-id="923c6-150">localhost</span></span>  
    > -   <span data-ttu-id="923c6-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="923c6-151">127.0.0.1</span></span>  
    > -   <span data-ttu-id="923c6-152">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="923c6-152">www.contoso.com</span></span>  
    > -   <span data-ttu-id="923c6-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="923c6-153">ContosoWeb01</span></span>  
  
4.  <span data-ttu-id="923c6-154">Son filtre özel üst bilgi içermeyen genel uç noktada gelen iletileri yönlendirme desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="923c6-155">Bu senaryo için iletileri regularCalc ve roundingCalc hizmetleri arasında alternatif.</span><span class="sxs-lookup"><span data-stu-id="923c6-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="923c6-156">"Hepsini bir kez deneme" Bu iletilerin yönlendirme desteklemek için işlenen her ileti için eşleştirecek bir filtre örneğini sağlayan özel bir filtre kullanın.</span><span class="sxs-lookup"><span data-stu-id="923c6-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="923c6-157">Bunlar diğer arasında alternatif olduğunu göstermek için hangi birlikte gruplandırılmış bir RoundRobinMessageFilter, iki örneğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="923c6-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="923c6-158">Çalışma zamanı sırasında bu filtre türü bu türdeki bir koleksiyona aynı grubu olarak yapılandırıldığı tüm tanımlı filtre örnekleri arasında geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="923c6-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="923c6-159">Bu, bu özel filtre döndürme arasında alternatif tarafından işlenen iletilerin neden olur `true` RoundRobinFilter1 ve RoundRobinFilter2.</span><span class="sxs-lookup"><span data-stu-id="923c6-159">This causes messages processed by this custom filter to alternate between returning `true` for RoundRobinFilter1 and RoundRobinFilter2.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="923c6-160">Filtre tabloları tanımlayın</span><span class="sxs-lookup"><span data-stu-id="923c6-160">Define Filter Tables</span></span>  
  
1.  <span data-ttu-id="923c6-161">Filtreler belirli istemci uç ile ilişkilendirmek için filtre tablo içinde yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="923c6-162">Bu örnek senaryo, filtreleri işlenme sırasını göstermek izin veren, isteğe bağlı bir ayardır filtre öncelik ayarları, ayrıca kullanır.</span><span class="sxs-lookup"><span data-stu-id="923c6-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="923c6-163">Hiçbir filtre öncelik belirtilmişse, tüm filtreleri eşzamanlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="923c6-164">Belirtildiğinde bir filtre öncelik sayesinde, hangi filtrelerin sırasını denetlemek için işlenen yönlendirme hizmeti performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="923c6-165">Filtre önceliklerin kullanımı gerekli olmamasını sağlamak mümkün olduğunda, filtre mantığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="923c6-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="923c6-166">Aşağıdaki filtre tablosunda tanımlar ve "tablosuna 2 önceliği daha önce tanımlanan XPathFilterElement" ekler.</span><span class="sxs-lookup"><span data-stu-id="923c6-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="923c6-167">Bu giriş, ayrıca "XPathFilterElement" iletisi eşleşirse, ileti "roundingCalcEndpoint" yönlendirilir belirtir</span><span class="sxs-lookup"><span data-stu-id="923c6-167">This entry also specifies that if the "XPathFilter" matches the message, the message will be routed to the "roundingCalcEndpoint"</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="923c6-168">Bir filtre öncelik belirtirken, en yüksek öncelik filtreleri önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="923c6-169">Bir veya daha fazla filtre belirli öncelik düzeyindeki eşleşirse hiçbir filtre öncelik düzeylerinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="923c6-170">Bu senaryo için 2, belirtilen en yüksek önceliktir ve bu düzeyde yalnızca filtre giriş budur.</span><span class="sxs-lookup"><span data-stu-id="923c6-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2.  <span data-ttu-id="923c6-171">Filtre girişleri, uç nokta adı veya adresi öneki inceleyerek bir ileti belirli bir noktadaki alınırsa, görmek için tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="923c6-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="923c6-172">Aşağıdaki girdileri bu filtre girişleri her ikisi de filtre tabloya ekleyin ve bunları ileti için yönlendirilmiş hedef uç noktaları ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="923c6-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="923c6-173">Bu filtreler, önceki XPath filtresi ileti eşleşmedi varsa bunlar yalnızca çalışması gerektiğini belirtmek için bir öncelik 1 ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="923c6-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="923c6-174">Bu filtreler, filtre önceliği 1 olduğundan, bunlar öncelik düzeyini 2'deki filtreyi ileti eşleşmiyorsa yalnızca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="923c6-175">Her iki filtreleri aynı öncelik düzeyine sahip olduğundan Ayrıca, bunlar aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="923c6-176">Her iki filtreleri birbirini dışlayan olduğundan, tek veya başka bir ileti eşleşecek şekilde mümkündür.</span><span class="sxs-lookup"><span data-stu-id="923c6-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3.  <span data-ttu-id="923c6-177">Bir ileti önceki filtrelerden biriyle eşleşmiyorsa, ileti genel hizmet uç noktası aracılığıyla alındı ve yönlendirmek yeri gösteren hiçbir üst bilgileri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="923c6-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="923c6-178">Bu iletiler, bunları iki hesaplayıcı hizmetleri arasında hangi yükünü dengeleyen özel filtre tarafından işleneceğini üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="923c6-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="923c6-179">Aşağıdaki örnek Filtresi tablosu için filtre girişleri ekleneceği gösterilmektedir; Her filtre iki hedef uç noktalardan biri ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="923c6-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="923c6-180">Bu girişler 0 önceliğini belirttiğinden, bunlar daha yüksek bir öncelik hiçbir filtre ileti eşleşiyorsa yalnızca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="923c6-181">Ayrıca, bunların her ikisi de aynı önceliği olduğundan, eşzamanlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="923c6-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="923c6-182">Daha önce belirtildiği gibi bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir ya da diğer olarak değerlendirir `true` alınan her ileti için.</span><span class="sxs-lookup"><span data-stu-id="923c6-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="923c6-183">Bu filtre ile aynı belirtilen grup ayarı kullanarak yalnızca iki filtre tanımlı olduğundan, yönlendirme hizmeti regularCalcEndpoint ve RoundingCalcEndpoint gönderme arasında diğerleri etkisidir.</span><span class="sxs-lookup"><span data-stu-id="923c6-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4.  <span data-ttu-id="923c6-184">Filtrelerle iletileri değerlendirmek için filtre tablonun ilk iletileri almak için kullanılan hizmet uç noktaları ile ilişkilendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="923c6-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="923c6-185">Aşağıdaki örnek, yönlendirme davranışını kullanarak yönlendirme tablosunu hizmet uç noktaları ile ilişkilendirmek gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="923c6-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="923c6-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="923c6-186">Example</span></span>  
 <span data-ttu-id="923c6-187">Yapılandırma dosyası tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="923c6-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="923c6-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="923c6-188">See Also</span></span>  
 [<span data-ttu-id="923c6-189">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="923c6-189">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
