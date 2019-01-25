---
title: 'Nasıl yapılır: Hizmet Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: b02031493df1a63f62b4bdab80b56b1fb220aa92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700604"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="01bae-102">Nasıl yapılır: Hizmet Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01bae-102">How To: Service Versioning</span></span>
<span data-ttu-id="01bae-103">Bu konuda aynı hizmetin farklı sürümlerine iletileri yönlendiren bir yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01bae-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="01bae-104">Bu örnekte, iki farklı sürümlerine bir hesap makinesi hizmet iletileri yönlendirilir `roundingCalc` (v1) ve `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="01bae-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="01bae-105">Hem uygulamalar aynı işlemleri desteği: Ancak, eski hizmet `roundingCalc`, sonuç döndürülmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="01bae-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="01bae-106">Yeni kullanılıp kullanılmayacağını belirtmek bir istemci uygulaması erişebilmelidir `regularCalc` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="01bae-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="01bae-107">Bir özel hizmet sürümünden bir ileti yönlendirmek için yönlendirme hizmeti ileti içeriğine göre ileti hedef belirlemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01bae-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="01bae-108">Aşağıda gösterilen yöntemi, istemci, sürüm bilgileri bir ileti üst bilgisi ekleyerek belirtin.</span><span class="sxs-lookup"><span data-stu-id="01bae-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="01bae-109">Ek veri iletmek istemcileri gerektirmeyen hizmet sürümü oluşturma yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="01bae-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="01bae-110">Örneğin, bir ileti için en son yönlendirilebilir veya bir hizmet veya yönlendirici en uyumlu sürümü standart SOAP Zarfı parçası kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="01bae-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="01bae-111">Her iki hizmet tarafından sunulan işlemleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="01bae-111">The operations exposed by both services are:</span></span>  
  
-   <span data-ttu-id="01bae-112">Ekle</span><span class="sxs-lookup"><span data-stu-id="01bae-112">Add</span></span>  
  
-   <span data-ttu-id="01bae-113">Çıkarma</span><span class="sxs-lookup"><span data-stu-id="01bae-113">Subtract</span></span>  
  
-   <span data-ttu-id="01bae-114">Çarp</span><span class="sxs-lookup"><span data-stu-id="01bae-114">Multiply</span></span>  
  
-   <span data-ttu-id="01bae-115">Bölme</span><span class="sxs-lookup"><span data-stu-id="01bae-115">Divide</span></span>  
  
 <span data-ttu-id="01bae-116">Her iki hizmet uygulamalarını aynı işlemleri işlemek ve dışında döndürmeleri veri temel olarak aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemek olanak tanımak için benzersiz değil İstek.</span><span class="sxs-lookup"><span data-stu-id="01bae-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="01bae-117">Örneğin, eylem filtrelerini her iki hizmet için varsayılan Eylemler aynı olduğundan kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="01bae-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="01bae-118">Yönlendirici hizmetinin her sürüm için belirli bir uç noktada kullanıma veya hizmet sürümü belirten iletiyi için özel üstbilgi öğesi ekleme gibi çeşitli şekillerde çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="01bae-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="01bae-119">Bu yaklaşımların her birinin benzersiz bir şekilde hizmetin belirli bir sürüme gelen iletileri yönlendirmek sağlar, ancak benzersiz ileti içeriğini kullanan istekler için farklı hizmet sürümleri arasında ayrım yapma, tercih edilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="01bae-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="01bae-120">Bu örnekte istemci uygulaması için istek iletisi 'CalcVer' özel üst bilgi ekler.</span><span class="sxs-lookup"><span data-stu-id="01bae-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="01bae-121">Bu üst bilgi iletisi için yönlendirileceğini hizmetinin sürümü belirten bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="01bae-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="01bae-122">Değerini '1', '2' değerini regularCalc hizmeti çağrılırken, ileti roundingCalc hizmeti tarafından işlenen gerekir gösterir.</span><span class="sxs-lookup"><span data-stu-id="01bae-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="01bae-123">Bu iletiyi hizmetin hangi sürümünün işleyecek doğrudan denetlemek istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bae-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="01bae-124">Özel üst bilgi iletisi içinde yer alan bir değer olduğundan, her iki hizmeti sürümleri hedefleyen iletileri almak için bir uç nokta kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01bae-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="01bae-125">Aşağıdaki kod, bu özel üstbilgi iletiye eklemek için istemci uygulamasında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="01bae-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="01bae-126">Uygulama hizmet sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="01bae-126">Implement Service Versioning</span></span>  
  
1.  <span data-ttu-id="01bae-127">Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktası belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="01bae-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="01bae-128">Aşağıdaki örnek, iletileri almak için kullanılacak bir tek hizmet uç noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01bae-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="01bae-129">Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar `roundingCalc` (v1) ve `regularCalc` (v2) Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="01bae-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
    ```xml  
    <services>  
        <service behaviorConfiguration="routingConfiguration"  
                 name="System.ServiceModel.Routing.RoutingService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost/routingservice/router" />  
            </baseAddresses>  
          </host>  
          <!--Set up the inbound endpoint for the Routing Service-->  
          <endpoint address="calculator"  
                    binding="wsHttpBinding"  
                    name="routerEndpoint"  
                    contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2.  <span data-ttu-id="01bae-130">Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01bae-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="01bae-131">Bu örnekte, XPath filtresi, hangi sürümü için ileti yönlendirileceğini belirlemek için "CalcVer" özel üst bilgi değeri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01bae-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="01bae-132">Bir XPath filtresi "CalcVer" üst bilgi içermeyen iletilerini algılamak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01bae-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="01bae-133">Aşağıdaki örnek, ad alanı tablosu ve gerekli filtreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01bae-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="01bae-134">S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve ad alanını temsil eden `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="01bae-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3.  <span data-ttu-id="01bae-135">Her filtre bir istemci uç noktası ile ilişkilendirir filtre tablo tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="01bae-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="01bae-136">İleti "CalcVer" üst bilgi değeri 1 ile içeriyorsa regularCalc hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="01bae-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="01bae-137">Başlığı 2 değerini içeriyorsa, roundingCalc hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="01bae-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="01bae-138">Üst bilgi varsa, ileti için regularCalc yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01bae-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="01bae-139">Aşağıdaki filtre tabloyu tanımlayan ve daha önce tanımlanan filtreler ekler.</span><span class="sxs-lookup"><span data-stu-id="01bae-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="01bae-140">Filtre tablosunda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="01bae-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="01bae-141">Aşağıdaki örnek, ilişkilendirme gösterir `filterTable1` hizmet uç noktaları ile:</span><span class="sxs-lookup"><span data-stu-id="01bae-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="01bae-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="01bae-142">Example</span></span>  
 <span data-ttu-id="01bae-143">Yapılandırma dosyasının tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bae-143">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
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
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="01bae-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="01bae-144">Example</span></span>  
 <span data-ttu-id="01bae-145">İstemci uygulamasının tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bae-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to   
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="01bae-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01bae-146">See also</span></span>
- [<span data-ttu-id="01bae-147">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="01bae-147">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
