---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: filtreleri kullanma'
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 0218685cae6fe8dc4c1e36e51075d58b041ae7fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734327"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="911bd-103">Nasıl yapılır: Filtreleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="911bd-103">How To: Use Filters</span></span>

<span data-ttu-id="911bd-104">Bu konuda, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="911bd-104">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="911bd-105">Bu örnekte, iletiler, regularCalc ve roundingCalc hesap makinesi hizmetinin iki uygulamasına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-105">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="911bd-106">Her iki uygulama da aynı işlemleri destekler; Ancak, bir hizmet, döndürmeden önce tüm hesaplamaları en yakın tamsayı değerine yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-106">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="911bd-107">İstemci uygulaması, hizmetin yuvarlama sürümünün kullanılıp kullanılmayacağını belirtebilmelidir; hiçbir hizmet tercihi ifade Ediyse, ileti iki hizmet arasında yük dengelemesi yapılır.</span><span class="sxs-lookup"><span data-stu-id="911bd-107">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="911bd-108">Her iki hizmet tarafından kullanıma sunulan işlemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="911bd-108">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="911bd-109">Ekle</span><span class="sxs-lookup"><span data-stu-id="911bd-109">Add</span></span>  
  
- <span data-ttu-id="911bd-110">Çıkar</span><span class="sxs-lookup"><span data-stu-id="911bd-110">Subtract</span></span>  
  
- <span data-ttu-id="911bd-111">Çarp</span><span class="sxs-lookup"><span data-stu-id="911bd-111">Multiply</span></span>  
  
- <span data-ttu-id="911bd-112">Böl</span><span class="sxs-lookup"><span data-stu-id="911bd-112">Divide</span></span>  
  
 <span data-ttu-id="911bd-113">Her iki hizmet de aynı işlemleri uygulayacağından, iletide belirtilen eylem benzersiz olmayacak olduğundan, eylem filtresini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="911bd-113">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="911bd-114">Bunun yerine, iletilerin uygun uç noktalara yönlendirildiğinden emin olmak için ek iş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="911bd-114">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="911bd-115">Benzersiz verileri belirleme</span><span class="sxs-lookup"><span data-stu-id="911bd-115">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="911bd-116">Her iki hizmet uygulaması da aynı işlemleri yaptığından ve temelde geri aldıkları verilerden farklı olduklarından, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, isteğin nasıl yönlendirileceğini belirlemenizi sağlayacak kadar benzersiz değildir.</span><span class="sxs-lookup"><span data-stu-id="911bd-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="911bd-117">Ancak, istemci uygulaması iletiye benzersiz bir üstbilgi değeri eklerse, iletinin nasıl yönlendirildiğini öğrenmek için bu değeri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="911bd-117">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="911bd-118">Bu örnekte, istemci uygulamanın, yuvarlama Hesaplayıcı tarafından işlenmek üzere bir ileti gerekiyorsa, aşağıdaki kodu kullanarak özel bir üst bilgi ekler:</span><span class="sxs-lookup"><span data-stu-id="911bd-118">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="911bd-119">Artık bu üstbilgiye yönelik iletileri incelemek ve üstbilgiyi içeren iletileri roundCalc hizmetine yönlendirmek için XPath filtresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="911bd-119">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="911bd-120">Ayrıca, yönlendirme hizmeti, gelen iletileri istemci uygulamanın gönderdiği uç noktaya göre belirli bir Hesaplayıcı uygulamasına benzersiz şekilde yönlendirmek için EndpointName, EndpointAddress veya PrefixEndpointAddress filtreleriyle birlikte kullanılabilecek iki sanal hizmet uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="911bd-120">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="911bd-121">Uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="911bd-121">Define Endpoints</span></span>  
  
1. <span data-ttu-id="911bd-122">Yönlendirme hizmeti tarafından kullanılan uç noktaları tanımlarken, önce istemcileriniz ve hizmetleriniz tarafından kullanılan kanalın şeklini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="911bd-122">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="911bd-123">Bu senaryoda, her iki hedef hizmet de bir istek-yanıt deseninin kullanıldığı için <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="911bd-123">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="911bd-124">Aşağıdaki örnek, yönlendirme hizmeti tarafından sunulan hizmet uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-124">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
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
  
     <span data-ttu-id="911bd-125">Bu yapılandırmayla, yönlendirme hizmeti üç ayrı uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="911bd-125">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="911bd-126">Çalışma zamanı seçeneklerine bağlı olarak, istemci uygulaması bu adreslerden birine iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="911bd-126">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="911bd-127">"Sanal" hizmet uç noktalarından birine ulaşan iletiler ("yuvarlama/Hesaplayıcı" veya "normal/Hesaplayıcı"), ilgili Hesaplayıcı uygulamasına iletilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-127">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="911bd-128">İstemci uygulaması isteği belirli bir uç noktaya göndermezse, ileti genel uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-128">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="911bd-129">Seçtiğiniz uç nokta ne olursa olsun, istemci uygulaması iletinin yuvarlama Hesaplayıcı uygulamasına iletilmesi gerektiğini belirtmek için özel üst bilgiyi dahil etmek de tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-129">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="911bd-130">Aşağıdaki örnek, yönlendirme hizmetinin iletileri yönlendirdiğini istemci (hedef) uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-130">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
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
  
     <span data-ttu-id="911bd-131">Bu uç noktalar, belirli bir filtreyle eşleştiğinde iletinin gönderildiği hedef uç noktayı göstermek için filtre tablosunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="911bd-131">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="911bd-132">Filtre tanımlama</span><span class="sxs-lookup"><span data-stu-id="911bd-132">Define Filters</span></span>  
  
1. <span data-ttu-id="911bd-133">İstemci uygulamanın iletiye eklediği "Roundinghesaplayıcı" özel üstbilgisine göre iletileri yönlendirmek için, bu üst bilginin varlığını denetlemek üzere bir XPath sorgusu kullanan bir filtre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="911bd-133">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="911bd-134">Bu üstbilgi özel bir ad alanı kullanılarak tanımlandığından, XPath sorgusunda kullanılan "Custom" özel ad alanı önekini tanımlayan bir ad alanı girişi de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="911bd-134">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="911bd-135">Aşağıdaki örnek, gerekli Yönlendirme bölümünü, ad alanı tablosunu ve XPath filtresini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-135">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
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
  
     <span data-ttu-id="911bd-136">Bu **MessageFilter** , "yuvarlama" değeri içeren Iletide bir Roundinghesaplayıcı başlığına bakar.</span><span class="sxs-lookup"><span data-stu-id="911bd-136">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="911bd-137">Bu üstbilgi, istemci tarafından, iletinin roundingCalc hizmetine yönlendirildiğini belirtmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="911bd-137">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="911bd-138">S12 ad alanı ön eki, ad alanı tablosunda varsayılan olarak tanımlanır ve ad alanını temsil eder `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="911bd-138">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="911bd-139">Ayrıca, iki sanal uç noktasında alınan iletileri aramak için filtreler tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="911bd-139">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="911bd-140">İlk sanal uç nokta, "normal/Hesaplayıcı" uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="911bd-140">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="911bd-141">İstemci, iletinin regularCalc hizmetine yönlendirildiğini göstermek için istekleri bu uç noktaya gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-141">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="911bd-142">Aşağıdaki yapılandırma, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> Iletinin filterData içinde belirtilen ada sahip bir uç nokta üzerinden geldiğini öğrenmek için öğesini kullanan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-142">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="911bd-143">"Hesaplatorendpoint" adlı hizmet uç noktası tarafından bir ileti alındığında, bu filtre olarak değerlendirilir `true` .</span><span class="sxs-lookup"><span data-stu-id="911bd-143">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="911bd-144">Ardından, roundingEndpoint adresine gönderilen iletileri gösteren bir filtre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="911bd-144">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="911bd-145">İstemci bu uç noktaya istek göndererek, iletinin roundingCalc hizmetine yönlendirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="911bd-145">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="911bd-146">Aşağıdaki yapılandırma, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> iletinin "yuvarlama/Hesaplayıcı" uç noktasında geldiğini öğrenmek için öğesini kullanan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="911bd-146">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="911bd-147">İle başlayan bir adreste bir ileti alındığında, `http://localhost/routingservice/router/rounding/` Bu filtre **true** olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-147">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="911bd-148">Bu yapılandırma tarafından kullanılan temel adres `http://localhost/routingservice/router` ve roundingEndpoint için belirtilen adres "yuvarlama/Hesaplayıcı" olduğundan, bu uç nokta ile iletişim kurmak için kullanılan tam adres `http://localhost/routingservice/router/rounding/calculator` Bu filtreyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="911bd-148">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="911bd-149">Tek bir konağa, bir eşleşme gerçekleştirirken konak adı değerlendirilmez, çünkü tek bir ana bilgisayar, ana bilgisayara istemci uygulamasından başvurmanın geçerli yolları olabilecek çeşitli konak adları kullanılarak başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-149">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="911bd-150">Örneğin, aşağıdakilerin tümü aynı konağa başvurabilir:</span><span class="sxs-lookup"><span data-stu-id="911bd-150">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="911bd-151">localhost</span><span class="sxs-lookup"><span data-stu-id="911bd-151">localhost</span></span>  
    > - <span data-ttu-id="911bd-152">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="911bd-152">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="911bd-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="911bd-153">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="911bd-154">Son filtre, genel uç noktaya gelen iletilerin özel üstbilgi olmadan yönlendirilmesini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="911bd-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="911bd-155">Bu senaryo için, iletilerin regularCalc ve roundingCalc hizmetleri arasında alternatif olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="911bd-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="911bd-156">Bu iletilerin "hepsini bir kez deneme" öğesini desteklemek için, işlenen her ileti için bir filtre örneğinin eşleşmesini sağlayan bir özel filtre kullanın.</span><span class="sxs-lookup"><span data-stu-id="911bd-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="911bd-157">Aşağıda, bir RoundRobinMessageFilter öğesinin aralarında farklı olmaları gerektiğini göstermek için birlikte gruplanmış iki örneği tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="911bd-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
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
  
     <span data-ttu-id="911bd-158">Çalışma zamanı sırasında, bu filtre türü, aynı grup olarak yapılandırılmış bu türün tanımlanmış tüm filtre örnekleri arasında tek bir koleksiyonda alternatifleri vardır.</span><span class="sxs-lookup"><span data-stu-id="911bd-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="911bd-159">Bu `true` , ve için döndürme arasında alternatif olarak bu özel filtre tarafından işlenen mesajların oluşmasına neden olur `RoundRobinFilter1` `RoundRobinFilter2` .</span><span class="sxs-lookup"><span data-stu-id="911bd-159">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="911bd-160">Filtre tabloları tanımlama</span><span class="sxs-lookup"><span data-stu-id="911bd-160">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="911bd-161">Filtreleri belirli istemci uç noktalarıyla ilişkilendirmek için, bunları bir filtre tablosu içine yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="911bd-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="911bd-162">Bu örnek senaryo, filtrelerin işlenme sırasını belirtmenize izin veren isteğe bağlı bir ayar olan filtre öncelik ayarlarını da kullanır.</span><span class="sxs-lookup"><span data-stu-id="911bd-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="911bd-163">Filtre önceliği belirtilmemişse, tüm filtreler eşzamanlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="911bd-164">Filtre önceliği belirtildiğinde, filtrelerin işlenme sırasını denetlemenizi sağlar, bu da yönlendirme hizmetinin performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="911bd-165">Mümkün olduğunda, filtre önceliklerinin kullanılması gerekli olmadığından filtre mantığını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="911bd-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="911bd-166">Aşağıda, filtre tablosu tanımlanmaktadır ve daha önce tanımlanan "XPathFilter" öğesini bir önceliği 2 olan tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="911bd-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="911bd-167">Bu giriş Ayrıca, `XPathFilter` iletisi ile eşleşirse iletinin öğesine yönlendirildiğini belirtir `roundingCalcEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="911bd-167">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
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
  
     <span data-ttu-id="911bd-168">Filtre önceliği belirtirken, en yüksek öncelikli filtreler önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="911bd-169">Belirli bir öncelik düzeyinde bir veya daha fazla filtre eşleşiyorsa, daha düşük öncelikli düzeylerde hiçbir filtre değerlendirilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="911bd-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="911bd-170">Bu senaryoda, 2 belirtilen en yüksek önceliktir ve bu düzeyde tek filtre girişi budur.</span><span class="sxs-lookup"><span data-stu-id="911bd-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="911bd-171">Filtre girdileri, uç nokta adını veya adres önekini inceleyerek belirli bir uç noktada bir iletinin alınıp alınmadığını denetlemek üzere tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="911bd-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="911bd-172">Aşağıdaki girişler, bu filtre girdilerinin her ikisini de filtre tablosuna ekler ve bunları iletinin yönlendirileceği hedef uç noktalarla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="911bd-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="911bd-173">Bu filtreler, yalnızca önceki XPath filtresi iletiyle eşleşmezse çalışması gerektiğini belirtmek için 1 önceliğine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="911bd-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="911bd-174">Bu filtrelerin filtre önceliği 1 olduğundan, yalnızca öncelik düzeyi 2 ' deki filtre iletiyle eşleşmezse değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="911bd-175">Ayrıca, her iki filtrenin de aynı öncelik düzeyine sahip olduğu için aynı anda değerlendirilirler.</span><span class="sxs-lookup"><span data-stu-id="911bd-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="911bd-176">Her iki filtre de birbirini dışlamadığından, bir iletiyle eşleşmesi yalnızca bir veya diğeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="911bd-177">Bir ileti önceki filtrelerden hiçbiriyle eşleşmezse, ileti genel hizmet uç noktası aracılığıyla alındı ve bu, nereye yönlendirildiğini belirten hiçbir üstbilgi bilgisi içermiyordu.</span><span class="sxs-lookup"><span data-stu-id="911bd-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="911bd-178">Bu iletiler özel filtre tarafından işlenerek, yük, iki Hesaplayıcı hizmeti arasında dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="911bd-179">Aşağıdaki örnek, filtre girişlerinin filtre tablosuna nasıl ekleneceğini gösterir; Her filtre iki hedef uç noktasından biriyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="911bd-180">Bu girdiler 0 değerini belirttiğinden, yalnızca daha yüksek öncelikli bir filtrenin iletiyle eşleşmesi durumunda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="911bd-181">Ayrıca, her ikisi de aynı önceliğe sahip olduğundan, aynı anda değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="911bd-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="911bd-182">Daha önce bahsedildiği gibi, bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir veya diğer her ileti için bir veya diğerini değerlendirir `true` .</span><span class="sxs-lookup"><span data-stu-id="911bd-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="911bd-183">Bu filtre kullanılarak yalnızca iki filtre tanımlandığından, aynı belirtilen grup ayarıyla, bu, yönlendirme hizmetinin regularCalcEndpoint ve RoundingCalcEndpoint öğesine gönderme arasında değişiklik göstermesi durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="911bd-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="911bd-184">İletileri filtrelere karşı değerlendirmek için, önce filtre tablosunun ileti almak için kullanılacak hizmet uç noktaları ile ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="911bd-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="911bd-185">Aşağıdaki örnek yönlendirme davranışını kullanarak yönlendirme tablosunun hizmet uç noktalarıyla nasıl ilişkilendirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="911bd-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="911bd-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="911bd-186">Example</span></span>  

 <span data-ttu-id="911bd-187">Yapılandırma dosyasının tüm listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="911bd-187">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="911bd-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="911bd-188">See also</span></span>

- [<span data-ttu-id="911bd-189">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="911bd-189">Routing Services</span></span>](../samples/routing-services.md)
