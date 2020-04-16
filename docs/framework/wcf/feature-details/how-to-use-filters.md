---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 34ea961b0ef5db51efcae0b86f2c06171d6d756c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464110"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="21023-102">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="21023-102">How To: Use Filters</span></span>
<span data-ttu-id="21023-103">Bu konu, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımları özetler.</span><span class="sxs-lookup"><span data-stu-id="21023-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="21023-104">Bu örnekte, iletiler bir hesap makinesi hizmetinin iki uygulamasına yönlendirilir, düzenli Calc ve yuvarlamaCalc.</span><span class="sxs-lookup"><span data-stu-id="21023-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="21023-105">Her iki uygulama da aynı işlemleri destekler; ancak bir hizmet, dönmeden önce tüm hesaplamaları en yakın tümsabudeğere yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="21023-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="21023-106">İstemci uygulaması, hizmetin yuvarlama sürümünü kullanıp kullanmayacağını belirtebilmeli; hizmet tercihi ifade edilmezse, ileti iki hizmet arasında yük dengelenir.</span><span class="sxs-lookup"><span data-stu-id="21023-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="21023-107">Her iki hizmettarafından ortaya çıkarılan işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21023-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="21023-108">Ekle</span><span class="sxs-lookup"><span data-stu-id="21023-108">Add</span></span>  
  
- <span data-ttu-id="21023-109">Çıkar</span><span class="sxs-lookup"><span data-stu-id="21023-109">Subtract</span></span>  
  
- <span data-ttu-id="21023-110">Çarp</span><span class="sxs-lookup"><span data-stu-id="21023-110">Multiply</span></span>  
  
- <span data-ttu-id="21023-111">Böl</span><span class="sxs-lookup"><span data-stu-id="21023-111">Divide</span></span>  
  
 <span data-ttu-id="21023-112">İletide belirtilen eylem benzersiz olmadığından, her iki hizmet de aynı işlemleri uyguladığından, Eylem filtresini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="21023-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="21023-113">Bunun yerine iletilerin uygun uç noktalara yönlendirilmesini sağlamak için ek çalışma yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21023-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="21023-114">Benzersiz Verileri Belirleme</span><span class="sxs-lookup"><span data-stu-id="21023-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="21023-115">Her iki hizmet uygulaması da aynı işlemleri işlediği nden ve döndükleri veriler dışında temelde aynı olduğundan, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, isteği nasıl yönlendireceklerini belirlemenize izin verecek kadar benzersiz değildir.</span><span class="sxs-lookup"><span data-stu-id="21023-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="21023-116">Ancak istemci uygulaması iletiye benzersiz bir üstbilgi değeri eklerse, iletinin nasıl yönlendirilmesi gerektiğini belirlemek için bu değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21023-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="21023-117">Bu örnekte, istemci uygulaması nın iletinin yuvarlama hesap makinesi tarafından işlenmesi gerekiyorsa, aşağıdaki kodu kullanarak özel bir üstbilgi ekler:</span><span class="sxs-lookup"><span data-stu-id="21023-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="21023-118">Artık bu üstbilginin iletilerini incelemek ve üstbilgi içeren iletileri roundCalc hizmetine yönlendirmek için XPath filtresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21023-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="21023-119">Ayrıca Yönlendirme Hizmeti, gelen iletileri istemci uygulamasının isteği gönderdiği bitiş noktasına bağlı olarak belirli bir hesap makinesi uygulamasına benzersiz bir şekilde yönlendirmek için EndpointName, EndpointAddress veya PrefixEndpointAddress filtreleriyle kullanılabilecek iki sanal hizmet bitiş noktasını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="21023-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="21023-120">Uç Noktaları Tanımla</span><span class="sxs-lookup"><span data-stu-id="21023-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="21023-121">Yönlendirme Hizmeti tarafından kullanılan uç noktaları tanımlarken, öncelikle müşterileriniz ve hizmetleriniz tarafından kullanılan kanalın şeklini belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21023-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="21023-122">Bu senaryoda, hem hedef hizmetler bir istek-yanıt deseni kullanır, bu nedenle <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21023-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="21023-123">Aşağıdaki örnekte Yönlendirme Hizmeti tarafından maruz kalan hizmet bitiş noktaları tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21023-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="21023-124">Bu yapılandırmaile Yönlendirme Hizmeti üç ayrı uç noktayı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="21023-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="21023-125">Çalışma zamanı seçimlerine bağlı olarak, istemci uygulaması bu adreslerden birine ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="21023-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="21023-126">"Sanal" hizmet bitiş noktalarından birine ("yuvarlama/hesap makinesi" veya "normal/hesap makinesi") gelen iletiler ilgili hesap makinesi uygulamasına iletilir.</span><span class="sxs-lookup"><span data-stu-id="21023-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="21023-127">İstemci uygulaması isteği belirli bir bitiş noktasına göndermezse, ileti genel bitiş noktasına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="21023-128">Seçilen bitiş noktası ne olursa olsun, istemci uygulaması iletinin yuvarlama hesap makinesi uygulamasına iletilmesi gerektiğini belirtmek için özel üstbilgi eklemeyi de seçebilir.</span><span class="sxs-lookup"><span data-stu-id="21023-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="21023-129">Aşağıdaki örnek, Yönlendirme Hizmeti'nin iletileri yolettiği istemci (hedef) uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21023-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="21023-130">Bu uç noktalar, iletinin belirli bir filtreyle eşleştiğinde gönderildiği hedef bitiş noktasını belirtmek için filtre tablosunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21023-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="21023-131">Filtreleri Tanımla</span><span class="sxs-lookup"><span data-stu-id="21023-131">Define Filters</span></span>  
  
1. <span data-ttu-id="21023-132">İstemci uygulamasının iletiye eklediği "Yuvarlama Hesaplayıcısı" özel üstbilgisini temel alan iletileri yönlendirmek için, bu üstbilginin varlığını denetlemek için XPath sorgusu kullanan bir filtre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="21023-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="21023-133">Bu üstbilgi özel bir ad alanı kullanılarak tanımlandığı için, XPath sorgusunda kullanılan "özel" özel bir ad alanı öneki tanımlayan bir ad alanı girişi de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21023-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="21023-134">Aşağıdaki örnekte gerekli yönlendirme bölümü, ad alanı tablosu ve XPath filtresi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21023-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="21023-135">Bu **MessageFilter,** iletide "yuvarlama" değeri içeren bir Yuvarlama Hesaplayıcısı üstbilgisini arar.</span><span class="sxs-lookup"><span data-stu-id="21023-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="21023-136">Bu üstbilgi istemci tarafından iletinin yuvarlamaCalc hizmetine yönlendirilmesi gerektiğini belirtmek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21023-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="21023-137">s12 ad alanı öneki, ad alanı tablosunda varsayılan olarak `http://www.w3.org/2003/05/soap-envelope`tanımlanır ve ad alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21023-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="21023-138">Ayrıca, iki sanal uç noktada alınan iletileri arayan filtreleri de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21023-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="21023-139">İlk sanal bitiş noktası "normal/hesap makinesi" bitiş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="21023-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="21023-140">İstemci, iletinin normal Calc hizmetine yönlendirilmesi gerektiğini belirtmek için bu bitiş noktasına istekgönderebilir.</span><span class="sxs-lookup"><span data-stu-id="21023-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="21023-141">Aşağıdaki yapılandırma, iletinin <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> filterData'da belirtilen adı içeren bir bitiş noktasından gelip gelmediğini belirlemek için bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21023-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="21023-142">"CalculatorEndpoint" adlı hizmet bitiş noktası tarafından bir ileti alınırsa, `true`bu filtre .</span><span class="sxs-lookup"><span data-stu-id="21023-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="21023-143">Ardından, yuvarlama Bitiş Noktası'nın adresine gönderilen iletileri arayan bir filtre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="21023-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="21023-144">İstemci, iletinin yuvarlamaCalc hizmetine yönlendirilmesi gerektiğini belirtmek için bu bitiş noktasına istekgönderebilir.</span><span class="sxs-lookup"><span data-stu-id="21023-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="21023-145">Aşağıdaki yapılandırma, iletinin "yuvarlama/hesap makinesi" bitiş noktasına gelip gelmediğini belirlemek <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> için bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21023-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="21023-146">İleti ile `http://localhost/routingservice/router/rounding/` başlayan bir adreste alınırsa, bu filtre **doğru**olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="21023-147">Bu yapılandırma tarafından kullanılan temel `http://localhost/routingservice/router` adres olduğundan ve yuvarlama Bitiş Noktası için belirtilen adres "yuvarlama/hesap makinesi" `http://localhost/routingservice/router/rounding/calculator`olduğundan, bu uç noktayla iletişim kurmak için kullanılan tam adres , bu filtreyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="21023-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="21023-148">PrefixEndpointAddress filtresi, tek bir ana bilgisayar istemci uygulamasından ana bilgisayara atıfta bulunarak geçerli yollar olabilecek çeşitli ana bilgisayar adları kullanılarak başvurulabileceğinden, bir eşleşme gerçekleştirirken ana bilgisayar adını değerlendirmez.</span><span class="sxs-lookup"><span data-stu-id="21023-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="21023-149">Örneğin, aşağıdakilerin tümü aynı ana bilgisayara başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="21023-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="21023-150">localhost</span><span class="sxs-lookup"><span data-stu-id="21023-150">localhost</span></span>  
    > - <span data-ttu-id="21023-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="21023-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="21023-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="21023-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="21023-153">Son filtre, özel üstbilgi olmadan genel bitiş noktasına gelen iletilerin yönlendirmesini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="21023-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="21023-154">Bu senaryo için, iletiler regularCalc ve yuvarlamaCalc hizmetleri arasında geçiş yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21023-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="21023-155">Bu iletilerin "yuvarlak robin" yönlendirmesini desteklemek için, işlenen her ileti için bir filtre örneğinin eşleşmesine izin veren özel bir filtre kullanın.</span><span class="sxs-lookup"><span data-stu-id="21023-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="21023-156">Aşağıda, aralarında geçiş olması gerektiğini belirtmek için birlikte gruplanan RoundRobinMessageFilter'in iki örneği tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21023-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="21023-157">Çalışma süresi sırasında, bu filtre türü, aynı grup olarak yapılandırılan bu türdeki tüm tanımlanmış filtre örnekleri arasında tek bir koleksiyona dönüşür.</span><span class="sxs-lookup"><span data-stu-id="21023-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="21023-158">Bu, bu özel filtre tarafından işlenen iletilerin `true` `RoundRobinFilter1` için `RoundRobinFilter2`dönen ve .</span><span class="sxs-lookup"><span data-stu-id="21023-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="21023-159">Filtre Tablolarını Tanımla</span><span class="sxs-lookup"><span data-stu-id="21023-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="21023-160">Filtreleri belirli istemci uç noktalarıyla ilişkilendirmek için, filtreleri bir filtre tablosuna yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21023-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="21023-161">Bu örnek senaryo, filtrelerin işlenme sırasını belirtmenize olanak tanıyan isteğe bağlı bir ayar olan filtre önceliği ayarlarını da kullanır.</span><span class="sxs-lookup"><span data-stu-id="21023-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="21023-162">Filtre önceliği belirtilmemişse, tüm filtreler aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="21023-163">Filtre önceliği belirtmek, filtrelerin işlendiği sırayı denetlemenize olanak sağlarken, Yönlendirme Hizmeti'nin performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="21023-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="21023-164">Mümkün olduğunda, filtre önceliklerinin kullanılmasının gerekli olmaması için filtre mantığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="21023-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="21023-165">Aşağıdaki filtre tablosunu tanımlar ve daha önce tanımlanan "XPathFilter"i 2 önceliği olan tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="21023-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="21023-166">Bu giriş ayrıca, iletiyle `XPathFilter` eşleşirse, iletinin `roundingCalcEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="21023-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="21023-167">Filtre önceliği belirtilirken, önce en yüksek öncelik filtreleri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="21023-168">Belirli bir öncelik düzeyinde bir veya daha fazla filtre eşleşirse, daha düşük öncelik düzeylerindeki filtreler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="21023-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="21023-169">Bu senaryo için, 2 belirtilen en yüksek önceliktir ve bu düzeydeki tek filtre girişidir.</span><span class="sxs-lookup"><span data-stu-id="21023-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="21023-170">Filtre girişleri, bitiş noktası adını veya adres önekini inceleyerek belirli bir uç noktadan ileti alınıp alınıp alınıp alınıp alınıp alınıp alınmayolmadığını denetlemek için tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="21023-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="21023-171">Aşağıdaki girişler, bu filtre girişlerinin her ikisini de filtre tablosuna ekler ve iletinin yönlendirileceği hedef uç noktalarıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="21023-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="21023-172">Bu filtreler, yalnızca önceki XPath filtresi iletiyle eşleşmediyse çalışması gerektiğini belirtmek için 1 önceliğe ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21023-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="21023-173">Bu filtrelerin filtre önceliği 1 olduğundan, yalnızca öncelik düzeyi 2'deki filtre iletiyle eşleşmiyorsa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="21023-174">Ayrıca, her iki filtre de aynı öncelik düzeyine sahip olduğundan aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="21023-175">Her iki filtre de birbirini dışladığından, yalnızca birinin veya diğerinin bir iletiyi eşleştirmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="21023-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="21023-176">İleti önceki filtrelerden herhangi biri ile eşleşmiyorsa, ileti genel hizmet bitiş noktası üzerinden alındı ve iletinin nereye yönlendirilmeyeceğini gösteren üstbilgi bilgisi içermedi.</span><span class="sxs-lookup"><span data-stu-id="21023-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="21023-177">Bu iletiler, iki hesap makinesi hizmeti arasında yük dengeleri özel filtre tarafından işlenecek.</span><span class="sxs-lookup"><span data-stu-id="21023-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="21023-178">Aşağıdaki örnek, filtre girişlerinin filtre tablosuna nasıl ekleyeceğini gösterir; her filtre iki hedef uç noktadan biriyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="21023-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="21023-179">Bu girişler 0 önceliği belirttiğinden, yalnızca daha yüksek bir önceliğe ait bir filtre iletiyle eşleşmediğinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="21023-180">Ayrıca, her ikisi de aynı önceliğe ait olduğundan, aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="21023-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="21023-181">Daha önce de belirtildiği gibi, bu filtre tanımları tarafından kullanılan özel `true` filtre, alınan her ileti için yalnızca bir veya diğerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="21023-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="21023-182">Bu filtre kullanılarak, aynı belirtilen grup ayarına sahip yalnızca iki filtre tanımlandığı için, bunun etkisi, Yönlendirme Hizmetinin düzenli CalcEndpoint'e gönderme ile YuvarlamaCalcEndpoint arasında dönüşümlü olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="21023-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="21023-183">İletileri filtrelere karşı değerlendirmek için, filtre tablosunun öncelikle ileti almak için kullanılacak hizmet bitiş noktalarıyla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="21023-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="21023-184">Aşağıdaki örnek, yönlendirme davranışını kullanarak yönlendirme tablosunun hizmet bitiş noktalarıyla nasıl ilişkilendirilen</span><span class="sxs-lookup"><span data-stu-id="21023-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="21023-185">Örnek</span><span class="sxs-lookup"><span data-stu-id="21023-185">Example</span></span>  
 <span data-ttu-id="21023-186">Aşağıda yapılandırma dosyasının tam listesi veremivettir.</span><span class="sxs-lookup"><span data-stu-id="21023-186">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21023-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21023-187">See also</span></span>

- [<span data-ttu-id="21023-188">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="21023-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
