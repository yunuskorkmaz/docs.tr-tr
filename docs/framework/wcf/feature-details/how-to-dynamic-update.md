---
title: 'Nasıl yapılır: Dinamik Güncelleme'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: aaeb4d9d42c289cf34a6aee9212fc2d74b8f8c01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184958"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="8e72e-102">Nasıl yapılır: Dinamik Güncelleme</span><span class="sxs-lookup"><span data-stu-id="8e72e-102">How To: Dynamic Update</span></span>
<span data-ttu-id="8e72e-103">Bu konu, yönlendirme yapılandırmasını oluşturmak ve dinamik olarak güncelleştirmek için gereken temel adımları özetler.</span><span class="sxs-lookup"><span data-stu-id="8e72e-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="8e72e-104">Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından elde edilir ve tüm iletileri normal Calc hesap makinesi hizmetine yönlendirir; ancak, daha sonra hedef bitiş noktası yuvarlamaCalc hizmeti değiştirmek için programlı olarak güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e72e-105">Birçok uygulamada, yapılandırma tamamen dinamik olur ve varsayılan yapılandırmaya güvenmez; ancak, hizmet başlatıldığında varsayılan yapılandırma durumu olması nın arzu edildiği bu konudaki gibi bazı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e72e-106">Dinamik güncelleştirmeler yalnızca bellekte gerçekleşir ve yapılandırma dosyalarının değiştirilmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="8e72e-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="8e72e-107">Hem regularCalc hem de roundingCalc aynı ekleme, çıkarma, çarpma ve bölme işlemlerini destekler; ancak, yuvarlamaCalc dönmeden önce tüm hesaplamaları en yakın tümsakaradeğere yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="8e72e-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="8e72e-108">Tüm iletileri normal Calc hizmetine yönlendirecek şekilde hizmeti yapılandırmak için bir yapılandırma dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="8e72e-109">Yönlendirme Hizmeti başlatıldıktan sonra, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> iletileri yuvarlama Calc hizmetine yönlendirmek için hizmeti yeniden yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="8e72e-110">İlk Yapılandırmayı Uygula</span><span class="sxs-lookup"><span data-stu-id="8e72e-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="8e72e-111">Hizmettarafından açığa çıkarılan hizmet bitiş noktalarını belirterek temel Yönlendirme Hizmeti Yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8e72e-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="8e72e-112">Aşağıdaki örnek, ileti leri almak için kullanılacak tek bir hizmet bitiş noktasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e72e-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="8e72e-113">Ayrıca, düzenli Calc'ye ileti göndermek için kullanılacak bir istemci bitiş noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e72e-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2. <span data-ttu-id="8e72e-114">İletileri hedef uç noktalarına yönlendirmek için kullanılan filtreyi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8e72e-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="8e72e-115">Bu örnekte, MatchAll filtresi tüm iletileri daha önce tanımlanan calcEndpoint'e yönlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="8e72e-116">Aşağıdaki örnekte filtre ve filtre tablosu tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3. <span data-ttu-id="8e72e-117">Gelen iletileri filtre tablosunda bulunan filtrelere göre değerlendirmek için yönlendirme davranışını kullanarak filtre tablosunu hizmet bitiş noktalarıyla ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="8e72e-118">Aşağıdaki örnekte, "filterTable1" ile hizmet bitiş noktası ilişkilendirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="8e72e-119">Dinamik Yapılandırma uygulayın</span><span class="sxs-lookup"><span data-stu-id="8e72e-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="8e72e-120">Yönlendirme Hizmetinin dinamik yapılandırması yalnızca yeni <xref:System.ServiceModel.Routing.RoutingConfiguration> bir oluşturma ve <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmayı değiştirmek için kullanılarak kod olarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="8e72e-121">Bu örnekte, Yönlendirme Hizmeti bir konsol uygulaması içinde kendi kendine barındırılan.</span><span class="sxs-lookup"><span data-stu-id="8e72e-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="8e72e-122">Uygulama başladıktan sonra, iletilerin yönlendirildiği hedef bitiş noktasını yapılandırmak için konsol penceresine 'normal' veya 'yuvarlama' girerek yönlendirme yapılandırmasını değiştirebilirsiniz; regularCalc 'normal' girildiğinde, aksi takdirde 'yuvarlama' girildiğinde Calc yuvarlama.</span><span class="sxs-lookup"><span data-stu-id="8e72e-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="8e72e-123">Yönlendirme Hizmetini desteklemek için aşağıdaki ifadeler eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="8e72e-124">Aşağıdaki kod, Yönlendirme Hizmetini konsol uygulaması olarak kendi kendine barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="8e72e-125">Bu, uygulama yapılandırma dosyasında bulunan önceki adımda açıklanan yapılandırmayı kullanarak Yönlendirme Hizmeti'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="8e72e-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="8e72e-126">While döngüsü yönlendirme yapılandırmasını değiştirmek için kullanılan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3. <span data-ttu-id="8e72e-127">Yönlendirme yapılandırmasını dinamik olarak güncelleştirmek için yeni bir yönlendirme yapılandırması oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="8e72e-128">Bu, varolan yönlendirme yapılandırmasının tamamen yerini alacağı için, yeni yönlendirme yapılandırması için gereken tüm uç noktaları, filtreleri ve filtre tablolarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="8e72e-129">Yeni yönlendirme yapılandırmasını kullanmak için, yeni <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yapılandırmayı çağırmanız ve geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e72e-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="8e72e-130">Hizmetin kullanıcı girişine göre yeniden yapılandırılabilmesi için daha önce tanımlanan while döngüsüne aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8e72e-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    > <span data-ttu-id="8e72e-131">Yeni bir YönlendirmeYapılandırması sağlama yöntemi RoutingExtension hizmet uzantısında bulunduğundan, Yeni RoutingConfiguration nesneleri WCF genişletilebilirlik modelinde ServiceHost veya ServiceExtensions (başka bir ServiceExtension gibi).</span><span class="sxs-lookup"><span data-stu-id="8e72e-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="8e72e-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e72e-132">Example</span></span>  

<span data-ttu-id="8e72e-133">Aşağıdaki, bu örnekte kullanılan konsol uygulamasının tam bir listesidir:</span><span class="sxs-lookup"><span data-stu-id="8e72e-133">The following is a complete listing of the console application used in this example:</span></span>
  
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
  
## <a name="example"></a><span data-ttu-id="8e72e-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e72e-134">Example</span></span>  

<span data-ttu-id="8e72e-135">Aşağıda, bu örnekte kullanılan yapılandırma dosyasının tam listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8e72e-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e72e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e72e-136">See also</span></span>

- [<span data-ttu-id="8e72e-137">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8e72e-137">Routing Services</span></span>](../samples/routing-services.md)
