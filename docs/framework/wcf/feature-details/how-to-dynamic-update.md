---
title: 'Nasıl yapılır: Dinamik Güncelleştirme'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 7e2fbd6c179444ef4c6e1df5e5068dbd1c5d29fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773056"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="2e794-102">Nasıl yapılır: Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="2e794-102">How To: Dynamic Update</span></span>
<span data-ttu-id="2e794-103">Bu konuda, oluşturmak ve dinamik yönlendirme yapılandırmasını güncelleştirmek için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e794-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="2e794-104">Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından alınır ve tüm iletileri regularCalc hesaplayıcı hizmete yönlendirir; Ancak, bu program aracılığıyla roundingCalc service hedef uç noktası değiştirmek üzere güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e794-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e794-105">Birçok uygulama, yapılandırma tamamen dinamik ve varsayılan yapılandırma üzerinde bağımlı kalmayacak; Ancak, hizmeti başladığında, varsayılan yapılandırma durumu etmesi olduğu gibi bu konuda, bir bazı senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="2e794-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e794-106">Dinamik güncelleştirme yalnızca bellekte oluşur ve yapılandırma dosyalarının değişiklik neden.</span><span class="sxs-lookup"><span data-stu-id="2e794-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="2e794-107">RegularCalc hem roundingCalc Ekle aynı işlemleri destekleyen, çıkarma, çarpma ve bölme; Ancak, roundingCalc döndürmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="2e794-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="2e794-108">Bir yapılandırma dosyası, hizmeti tüm iletileri regularCalc hizmetine yönlendirecek şekilde yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e794-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="2e794-109">Yönlendirme hizmeti başlatıldıktan sonra <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> roundingCalc hizmetine iletileri yönlendirmek için hizmeti yeniden yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e794-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="2e794-110">Başlangıç yapılandırmasını Uygula</span><span class="sxs-lookup"><span data-stu-id="2e794-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="2e794-111">Temel yönlendirme hizmeti yapılandırması hizmet tarafından sunulan hizmet uç noktaları belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e794-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="2e794-112">Aşağıdaki örnek, iletileri almak için kullanılacak bir tek hizmet uç noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e794-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="2e794-113">Ayrıca, regularCalc için ileti göndermek için kullanılan istemci uç noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e794-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
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
  
2. <span data-ttu-id="2e794-114">Hedef Uç noktalara iletileri yönlendirmek için kullanılan bir filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e794-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="2e794-115">Bu örnekte, MatchAll filtre önceden tanımlanmış regularCalcEndpoint tüm iletileri yönlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e794-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="2e794-116">Aşağıdaki örnek, filtreleme tablosu ve filtre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e794-116">The following example defines the filter and filter table.</span></span>  
  
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
  
3. <span data-ttu-id="2e794-117">Filtre tablosunda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2e794-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="2e794-118">Aşağıdaki örnek, hizmet uç noktası ile ilişkilendirmeyi "filterTable1" gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e794-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
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
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="2e794-119">Dinamik uygulama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2e794-119">Implement Dynamic Configuration</span></span>  
 <span data-ttu-id="2e794-120">Dinamik yönlendirme hizmeti yapılandırması yalnızca gerçekleştirilebilecek kod içinde yeni bir oluşturarak <xref:System.ServiceModel.Routing.RoutingConfiguration> ve kullanarak <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmasını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="2e794-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="2e794-121">Bu örnekte, yönlendirme hizmeti bir konsol uygulaması içinde şirket içinde barındırılan.</span><span class="sxs-lookup"><span data-stu-id="2e794-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="2e794-122">Uygulama başlatıldıktan sonra konsol penceresinde iletileri yönlendirilir hedef uç noktasını yapılandırmak için 'Normal' veya 'yuvarlama' girerek yönlendirme yapılandırmayı değiştirebilirsiniz; 'Normal'olduğunda ' regularCalc girilir, aksi takdirde 'yuvarlarken' roundingCalc girilir.</span><span class="sxs-lookup"><span data-stu-id="2e794-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="2e794-123">Aşağıdaki yönlendirme hizmetini desteklemek için using deyimlerini eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e794-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="2e794-124">Aşağıdaki kod, yönlendirme hizmeti bir konsol uygulaması olarak kendi kendine barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e794-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="2e794-125">Bu yönlendirme kullanarak uygulama yapılandırma dosyası içinde yer alan önceki adımda açıklanan Yapılandırma hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="2e794-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="2e794-126">While döngüsü yönlendirme yapılandırmasını değiştirmek için kullanılan kod içerir.</span><span class="sxs-lookup"><span data-stu-id="2e794-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
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
  
3. <span data-ttu-id="2e794-127">Dinamik yönlendirme yapılandırmasını güncelleştirmek için yeni bir yönlendirme yapılandırması oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e794-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="2e794-128">Mevcut yönlendirme yapılandırmasını tamamen değiştirecek şekilde bu tüm uç noktaları, filtreler ve yeni yönlendirme yapılandırma için gerekli olan filtre tabloları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2e794-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="2e794-129">Yeni yönlendirme yapılandırması kullanmak için çağırmalıdır <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> ve yeni yapılandırma geçişi.</span><span class="sxs-lookup"><span data-stu-id="2e794-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="2e794-130">Aşağıdaki kodu ekleyin while döngüsü hizmetinin yapılandırılması izin vermek için önceden tanımlanmış kullanıcı girişini temel alarak.</span><span class="sxs-lookup"><span data-stu-id="2e794-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
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
    > <span data-ttu-id="2e794-131">Sağlama yöntemini beri yeni RoutingConfiguration RoutingExtension hizmet uzantısı, yeni RoutingConfiguration nesneleri sağlanabilir herhangi bir ServiceHost başvuru elde edebilirsiniz veya WCF genişletilebilirlik modeli içinde bulunan veya ServiceExtensions (başka bir ServiceExtension gibi).</span><span class="sxs-lookup"><span data-stu-id="2e794-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="2e794-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e794-132">Example</span></span>  
 <span data-ttu-id="2e794-133">Bu örnekte kullanılan konsol uygulamasının tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e794-133">Following is a complete listing of the console application used in this example.</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="2e794-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e794-134">Example</span></span>  
 <span data-ttu-id="2e794-135">Yapılandırmayı tam bir listesi aşağıdadır Bu örnekte kullanılan dosya.</span><span class="sxs-lookup"><span data-stu-id="2e794-135">Following is a complete listing of the configuration file used in this example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e794-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e794-136">See also</span></span>

- [<span data-ttu-id="2e794-137">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2e794-137">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
