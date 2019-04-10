---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 5d3ed4a1d64edee274e60f5bf156b4294902df8c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295529"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="beec0-102">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="beec0-102">How To: Use Filters</span></span>
<span data-ttu-id="beec0-103">Bu konuda, birden çok filtre kullanan yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="beec0-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="beec0-104">Bu örnekte, iki hesap makinesi hizmeti, regularCalc ve roundingCalc uygulamaları için iletileri yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="beec0-105">Hem uygulamalar aynı işlemleri desteği: Ancak bir hizmet, döndürmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="beec0-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="beec0-106">Bir istemci uygulaması yuvarlama sürüm hizmetinin kullanılıp kullanılmayacağını belirtmek için bir değer olmalıdır; hiçbir hizmet tercihi ifade, ileti iki hizmet arasında yük dengeli yoktur.</span><span class="sxs-lookup"><span data-stu-id="beec0-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="beec0-107">Her iki hizmet tarafından sunulan işlemleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="beec0-107">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="beec0-108">Ekle</span><span class="sxs-lookup"><span data-stu-id="beec0-108">Add</span></span>  
  
-   <span data-ttu-id="beec0-109">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="beec0-109">Subtract</span></span>  
  
-   <span data-ttu-id="beec0-110">Çarp</span><span class="sxs-lookup"><span data-stu-id="beec0-110">Multiply</span></span>  
  
-   <span data-ttu-id="beec0-111">Bölme</span><span class="sxs-lookup"><span data-stu-id="beec0-111">Divide</span></span>  
  
 <span data-ttu-id="beec0-112">Her iki hizmet de aynı işlemleri uygulamak için eylem filtresi kullanamazsınız, çünkü message içinde belirtilen eylem benzersiz olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="beec0-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="beec0-113">Bunun yerine iletileri uygun Uç noktalara yönlendirilir emin olmak için ek bir iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="beec0-114">Benzersiz veri belirleme</span><span class="sxs-lookup"><span data-stu-id="beec0-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="beec0-115">Her iki hizmet uygulamalarını aynı işlemleri işlemek ve dışında döndürmeleri veri temel olarak aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemek olanak tanımak için benzersiz değil İstek.</span><span class="sxs-lookup"><span data-stu-id="beec0-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="beec0-116">Ancak daha sonra istemci uygulama bir benzersiz üstbilgi değerini ekler, ileti nasıl yönlendirileceğini belirlemek için bu değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beec0-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="beec0-117">İstemci uygulaması yuvarlama hesaplayıcı tarafından işlenecek ileti gerekiyorsa bu örnek için bir özel üst bilgi aşağıdaki kodu kullanarak ekler:</span><span class="sxs-lookup"><span data-stu-id="beec0-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="beec0-118">Artık bu üst bilgi iletilerini incelemek için XPath filtreyi kullanın ve roundCalc hizmetine üstbilgisini içeren iletiler yönlendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beec0-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="beec0-119">Ayrıca yönlendirme hizmeti EndpointAddress, Uçnoktaadı ile kullanılabilecek iki sanal hizmet uç noktalarını kullanıma sunar veya PrefixEndpointAddress benzersiz uç noktasına göre belirli hesaplayıcı uygulamasına gelen iletileri yönlendirmek için filtreler için istemci uygulaması isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="beec0-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="beec0-120">Uç noktalarını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="beec0-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="beec0-121">Yönlendirme hizmeti tarafından kullanılan uç noktalarını tanımlarken, istemcileri ve Hizmetleri tarafından kullanılan kanal şeklini ilk belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="beec0-122">Bu senaryoda, her iki hedef hizmetler bir istek-yanıt deseni kullanır. böylece <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="beec0-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="beec0-123">Aşağıdaki örnek, yönlendirme hizmeti tarafından kullanıma sunulan hizmet uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="beec0-124">Bu yapılandırma ile yönlendirme hizmeti, üç ayrı uç noktalarını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="beec0-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="beec0-125">Çalışma zamanı seçimlere bağlı olarak, istemci uygulama iletileri bu adreslerden birini gönderir.</span><span class="sxs-lookup"><span data-stu-id="beec0-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="beec0-126">("Yuvarlama/hesaplayıcı" veya "normal/hesaplayıcı") "sanal" hizmet uç noktalardan biri gelen iletiler için karşılık gelen hesaplayıcısı uygulaması iletilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="beec0-127">İstemci uygulama, belirli bir uç noktaya istek göndermediği durumlarda ileti genel uç noktaya değinilmiştir.</span><span class="sxs-lookup"><span data-stu-id="beec0-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="beec0-128">Seçilen uç nokta bağımsız olarak, istemci uygulaması, yuvarlama hesaplayıcı uygulamasına iletinin iletileceği belirtmek için özel üst bilgi eklemeyi de seçebilirler.</span><span class="sxs-lookup"><span data-stu-id="beec0-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="beec0-129">Aşağıdaki örnek, yönlendirme hizmeti, iletileri yönlendirir. (hedef) istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="beec0-130">Bu uç noktaları, filtre tablosunda, mesajın gönderilip gönderilmediği özgü süzgeçler eşleştiğinde hedef uç nokta belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="beec0-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="beec0-131">Filtreleri tanımlar</span><span class="sxs-lookup"><span data-stu-id="beec0-131">Define Filters</span></span>  
  
1. <span data-ttu-id="beec0-132">İstemci uygulaması ekler "RoundingCalculator" özel üst bilgi temel iletileri yönlendirmek için bu üst bilgisi varlığını denetlemek için bir XPath sorgusu kullanan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="beec0-133">Ayrıca özel bir ad alanı kullanarak bu başlığı tanımlı olduğundan, XPath sorgusundaki "kullanılan özel" bir özel ad alanı öneki tanımlayan bir ad alanı girişi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="beec0-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="beec0-134">Aşağıdaki örnek, gerekli yönlendirme bölümünde, ad alanı tablosu ve XPath filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="beec0-135">Bu **MessageFilter** RoundingCalculator başlığı "yuvarlama" bir değer içeren iletiyi arar.</span><span class="sxs-lookup"><span data-stu-id="beec0-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="beec0-136">Bu üst bilgi iletisi roundingCalc hizmete yönlendirileceğini göstermek için istemci tarafından ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="beec0-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="beec0-137">S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve ad alanını temsil eden `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="beec0-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="beec0-138">Ayrıca iki sanal uç noktalarda alınan iletilerin arayın filtreleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="beec0-139">İlk sanal uç "normal/hesaplayıcı" uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="beec0-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="beec0-140">İstemci istekleri ileti regularCalc hizmete yönlendirileceğini belirtmek için bu endpoint gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beec0-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="beec0-141">Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ileti filterData içinde belirtilen adla bir uç nokta gelen varsa belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="beec0-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="beec0-142">"CalculatorEndpoint" adlı hizmet uç noktası tarafından bir ileti alınmazsa, bu filtresinin `true`.</span><span class="sxs-lookup"><span data-stu-id="beec0-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="beec0-143">Ardından, roundingEndpoint adresine gönderilen iletileri bakan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="beec0-144">İstemci istekleri ileti roundingCalc hizmete yönlendirileceğini belirtmek için bu endpoint gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beec0-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="beec0-145">Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> iletinin "yuvarlama/hesaplayıcı" uç noktada geldiği varsa belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="beec0-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="beec0-146">İle başlayan bir adresteki bir ileti alındığında, `http://localhost/routingservice/router/rounding/` bu filtresinin sonra **true**.</span><span class="sxs-lookup"><span data-stu-id="beec0-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="beec0-147">Bu yapılandırma tarafından kullanılan temel adresi olduğundan `http://localhost/routingservice/router` ve roundingEndpoint "yuvarlama/hesap makinesi" için belirtilen adres, bu uç nokta ile iletişim kurmak için kullanılan tam adresidir `http://localhost/routingservice/router/rounding/calculator`, bu filtre ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="beec0-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="beec0-148">PrefixEndpointAddress filtresi ana bilgisayar adı, istemci uygulamasından konağa başvuran geçerli yolu olmalıdır çünkü tek bir ana bilgisayar için tüm olabilir ve ana bilgisayar adları çeşitli kullanılarak başvurulabilen bir eşleşme gerçekleştirme değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="beec0-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="beec0-149">Örneğin, aşağıdakilerin tümü aynı konağa başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="beec0-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    > -   <span data-ttu-id="beec0-150">localhost</span><span class="sxs-lookup"><span data-stu-id="beec0-150">localhost</span></span>  
    > -   <span data-ttu-id="beec0-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="beec0-151">127.0.0.1</span></span>  
    > -   `www.contoso.com`  
    > -   <span data-ttu-id="beec0-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="beec0-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="beec0-153">Son filtre özel üst bilgi içermeyen genel uç noktasında gelen iletileri yönlendirme desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="beec0-154">Bu senaryo için regularCalc ve roundingCalc hizmetleri arasında iletileri alternatif.</span><span class="sxs-lookup"><span data-stu-id="beec0-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="beec0-155">"Hepsini bir kez deneme" Bu iletilerin yönlendirme desteklemek için bir filtre örneğini işlenen her ileti için eşleşen izin veren özel bir filtre kullanın.</span><span class="sxs-lookup"><span data-stu-id="beec0-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="beec0-156">Bunlar diğer arasında alternatif olduğunu belirtmek için birlikte gruplanmış bir RoundRobinMessageFilter, iki örneğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beec0-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="beec0-157">Çalışma zamanı sırasında bu filtre türü, bu tür tek bir koleksiyonda aynı grup olarak yapılandırılmış tüm tanımlı filtre örnekleri arasında geçiş yapıyor.</span><span class="sxs-lookup"><span data-stu-id="beec0-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="beec0-158">Bu alternatif döndüren arasında bu özel filtre tarafından işlenen iletilerin neden `true` için `RoundRobinFilter1` ve `RoundRobinFilter2`.</span><span class="sxs-lookup"><span data-stu-id="beec0-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="beec0-159">Filtre tabloları tanımlama</span><span class="sxs-lookup"><span data-stu-id="beec0-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="beec0-160">Filtreler belirli istemci uç noktaları ile ilişkilendirmek için bir filtre tablosunun yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="beec0-161">Bu örnek senaryo, filtreleri işlenme sırasını belirtmenize olanak sağlayan, isteğe bağlı bir ayardır filtre öncelik ayarlarını da kullanır.</span><span class="sxs-lookup"><span data-stu-id="beec0-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="beec0-162">Hiçbir filtre öncelik belirtilmezse, tüm filtreleri eşzamanlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="beec0-163">Belirtirken bir filtre önceliğine izin verir, hangi filtrelerin sırasını denetlemek için işlenen, Yönlendirme Hizmeti performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="beec0-164">Filtre önceliklerin kullanımı gerekli değildir. böylece mümkün olduğunda, filtre mantığını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="beec0-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="beec0-165">Aşağıdaki filtre tabloyu tanımlayan ve "tablosuna bir öncelik 2 ile daha önce tanımlanan XPathFilterElement" ekler.</span><span class="sxs-lookup"><span data-stu-id="beec0-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="beec0-166">Bu giriş, ayrıca olmadığını belirtir `XPathFilter` eşleşen iletisi için ileti yönlendirilir `roundingCalcEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="beec0-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="beec0-167">Bir filtre öncelik belirtirken, en yüksek öncelikli filtreleri önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="beec0-168">Belirli bir öncelik düzeyinde bir veya daha fazla filtrelerle eşleşen, en düşük öncelik düzeyleri filtre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="beec0-169">Bu senaryo için belirtilen en yüksek öncelik 2. ve bu düzeyde yalnızca filtre giriş budur.</span><span class="sxs-lookup"><span data-stu-id="beec0-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="beec0-170">Filtre girişleri, uç nokta adı veya adres ön eki inceleyerek bir ileti belirli bir noktadaki alındığında, kontrol etmek için tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="beec0-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="beec0-171">Aşağıdaki girdileri hem de bu filtre girişleri filtre tabloya ekleyin ve bunları için ileti yönlendirilecek hedef uç noktaları ile ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="beec0-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="beec0-172">Bu filtreler, önceki XPath filtresi ileti eşleşmedi varsa bunlar yalnızca çalışması gerektiğini belirtmek için bir öncelik 1 için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="beec0-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="beec0-173">Bu filtreler, filtre önceliği 1 olduğundan, bunlar öncelik düzeyi 2 sırasında filtre ileti eşleşmiyorsa yalnızca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="beec0-174">Her iki filtreleri aynı öncelik düzeyine sahip olduğundan da, bunlar aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="beec0-175">Her iki filtreleri birbirini dışlayan olduğundan, tek veya başka bir ileti eşleştirilecek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="beec0-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="beec0-176">Bir ileti herhangi bir önceki süzgeçlere eşleşmiyorsa ileti genel hizmet uç noktası aracılığıyla alındı ve yönlendirmek yeri belirten hiçbir üst bilgiler.</span><span class="sxs-lookup"><span data-stu-id="beec0-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="beec0-177">Bu iletiler, bunları iki hesaplayıcı hizmetleri arasında yük dengeleyen özel filtre tarafından işlenmesi üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="beec0-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="beec0-178">Aşağıdaki örnek, filtre girişleri filtre tabloya eklenecek gösterilmektedir; Her bir filtrenin iki hedef uç noktalardan biri ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="beec0-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="beec0-179">Bu girişler bir öncelik 0 belirttiğinden, bunlar daha yüksek bir öncelik filtre ileti eşleşiyorsa yalnızca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="beec0-180">Ayrıca, bunlar her ikisi de aynı önceliği olduğundan, eşzamanlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="beec0-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="beec0-181">Daha önce belirtildiği gibi bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir ya da diğer olarak değerlendirir `true` alınan her ileti için.</span><span class="sxs-lookup"><span data-stu-id="beec0-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="beec0-182">Bu filtre ile aynı belirtilen grup ayarını kullanarak yalnızca iki filtre tanımlı olduğundan, yönlendirme hizmeti regularCalcEndpoint ve RoundingCalcEndpoint gönderme arasında diğerleri etkisidir.</span><span class="sxs-lookup"><span data-stu-id="beec0-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="beec0-183">Filtrelerle iletileri değerlendirmek için filtre tablonun ilk ileti almak için kullanılacak olan hizmet uç noktaları ile ilişkilendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="beec0-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="beec0-184">Aşağıdaki örnek, yönlendirme davranışını kullanarak hizmet uç noktaları ile yönlendirme tablosunu ilişkilendirme gösterir:</span><span class="sxs-lookup"><span data-stu-id="beec0-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="beec0-185">Örnek</span><span class="sxs-lookup"><span data-stu-id="beec0-185">Example</span></span>  
 <span data-ttu-id="beec0-186">Yapılandırma dosyasının tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="beec0-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="beec0-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beec0-187">See also</span></span>

- [<span data-ttu-id="beec0-188">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="beec0-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
