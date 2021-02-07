---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dinamik güncelleştirme'
title: 'Nasıl yapılır: Dinamik Güncelleştirme'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 877cb58dd271fa70176a4197da273d923ec253f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704725"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="d83d3-103">Nasıl yapılır: Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="d83d3-103">How To: Dynamic Update</span></span>

<span data-ttu-id="d83d3-104">Bu konuda, yönlendirme yapılandırmasını oluşturmak ve dinamik olarak güncelleştirmek için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-104">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="d83d3-105">Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından alınır ve tüm iletileri regularCalc Hesaplayıcı hizmetine yönlendirir; Ancak, bu daha sonra kaynak uç noktasını roundingCalc hizmeti değiştirmek için programlı olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-105">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d83d3-106">Birçok uygulamada, yapılandırma tamamen dinamik olur ve varsayılan bir yapılandırmaya güvenmeyecektir; Ancak, bu konu başlığı altında, hizmet başlatıldığında varsayılan bir yapılandırma durumuna sahip olmak istenen bazı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-106">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d83d3-107">Dinamik güncelleştirmeler yalnızca bellekte oluşur ve yapılandırma dosyalarının değiştirilmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="d83d3-107">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="d83d3-108">Hem regularCalc hem de roundingCalc, ekleme, çıkarma, çarpma ve bölme işlemlerini destekler; Ancak roundingCalc, döndürmeden önce tüm hesaplamaları en yakın tamsayı değerine yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="d83d3-108">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="d83d3-109">Bir yapılandırma dosyası, tüm iletileri regularCalc hizmetine yönlendirmek üzere hizmetini yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-109">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="d83d3-110">Yönlendirme hizmeti başlatıldıktan sonra, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> Iletileri roundingCalc hizmetine yönlendirmek üzere hizmeti yeniden yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-110">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="d83d3-111">Ilk yapılandırmayı Uygula</span><span class="sxs-lookup"><span data-stu-id="d83d3-111">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="d83d3-112">Hizmet tarafından sunulan hizmet uç noktalarını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d83d3-112">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="d83d3-113">Aşağıdaki örnek, ileti almak için kullanılacak tek bir hizmet uç noktasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d83d3-113">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="d83d3-114">Ayrıca, regularCalc 'e ileti göndermek için kullanılacak bir istemci uç noktası da tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d83d3-114">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="d83d3-115">İletileri hedef uç noktalara yönlendirmek için kullanılan filtreyi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d83d3-115">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="d83d3-116">Bu örnekte, tüm iletileri daha önce tanımlanan regularCalcEndpoint öğesine yönlendirmek için MatchAll filtresi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-116">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="d83d3-117">Aşağıdaki örnekte Filter ve Filter tablosu tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-117">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="d83d3-118">Gelen iletileri filtre tablosunda yer alan filtrelere karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-118">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d83d3-119">Aşağıdaki örnek, "filterTable1" ın hizmet uç noktasıyla ilişkilendirilmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-119">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="d83d3-120">Dinamik yapılandırmayı Uygula</span><span class="sxs-lookup"><span data-stu-id="d83d3-120">Implement Dynamic Configuration</span></span>  

 <span data-ttu-id="d83d3-121">Yönlendirme hizmetinin dinamik yapılandırması yalnızca yeni bir oluşturma <xref:System.ServiceModel.Routing.RoutingConfiguration> ve <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmayı değiştirmek için kullanılarak kod içinde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-121">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="d83d3-122">Bu örnekte, yönlendirme hizmeti bir konsol uygulaması içinde kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-122">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="d83d3-123">Uygulama başladıktan sonra, iletilerin yönlendirildiği hedef uç noktasını yapılandırmak için konsol penceresine ' Regular ' veya ' yuvarla ' girerek yönlendirme yapılandırmasını değiştirebilirsiniz; ' Regular ' girildiğinde regularCalc, aksi takdirde, ' yuvarlama ' girildiğinde roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="d83d3-123">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="d83d3-124">Yönlendirme hizmetini desteklemek için aşağıdaki using deyimleri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-124">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="d83d3-125">Aşağıdaki kod, yönlendirme hizmetini bir konsol uygulaması olarak kendine barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-125">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="d83d3-126">Bu, uygulama yapılandırma dosyası içinde yer alan önceki adımda açıklanan yapılandırmayı kullanarak yönlendirme hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="d83d3-126">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="d83d3-127">While döngüsü, yönlendirme yapılandırmasını değiştirmek için kullanılan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-127">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="d83d3-128">Yönlendirme yapılandırmasını dinamik olarak güncelleştirmek için yeni bir yönlendirme yapılandırmasının oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-128">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="d83d3-129">Bu, mevcut yönlendirme yapılandırmasının tamamen yerini alacak şekilde, yeni yönlendirme yapılandırması için gereken tüm uç noktaları, filtreleri ve filtre tablolarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-129">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="d83d3-130">Yeni yönlendirme yapılandırmasını kullanmak için <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> Yeni yapılandırmayı çağırmanız ve geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-130">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="d83d3-131">Hizmetin kullanıcı girişine göre yeniden yapılandırılması için aşağıdaki kodu daha önce tanımlanan while döngüsüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d83d3-131">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d83d3-132">Yeni bir RoutingConfiguration sağlama yöntemi RoutingExtension hizmeti uzantısında yer aldığı için, yeni RoutingConfiguration nesneleri, ServiceHost veya ServiceExtensions 'a (örneğin, başka bir ServiceExtension gibi) başvuru elde eden veya içeren WCF genişletilebilirlik modelinde herhangi bir yerde sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d83d3-132">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="d83d3-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d83d3-133">Example</span></span>  

<span data-ttu-id="d83d3-134">Bu örnekte kullanılan konsol uygulamasının tüm listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d83d3-134">The following is a complete listing of the console application used in this example:</span></span>
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d83d3-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="d83d3-135">Example</span></span>  

<span data-ttu-id="d83d3-136">Aşağıda, bu örnekte kullanılan yapılandırma dosyasının tamamen bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d83d3-136">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d83d3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d83d3-137">See also</span></span>

- [<span data-ttu-id="d83d3-138">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d83d3-138">Routing Services</span></span>](../samples/routing-services.md)
