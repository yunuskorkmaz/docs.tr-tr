---
title: "Nasıl yapılır: Dinamik Güncelleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 748286b4f6fa22b23423ff5c176c76d11fbe742d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamic-update"></a>Nasıl yapılır: Dinamik Güncelleme
Bu konuda oluşturmak ve dinamik yönlendirme yapılandırmasını güncelleştirmek için gereken temel adımlar verilmiştir. Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından alınır ve tüm iletileri regularCalc hesaplayıcı hizmete yönlendirir; Ancak, daha sonra program aracılığıyla hedef uç nokta roundingCalc hizmet değiştirmek için güncelleştirilir.  
  
> [!NOTE]
>  Birçok uygulamalarında yapılandırma tam olarak dinamik olacaktır ve bir varsayılan yapılandırmasını kullanan değil; Ancak, hizmeti başladığında varsayılan yapılandırma durumu etmesi olduğu Bu konu, bir gibi bazı senaryolar vardır.  
  
> [!NOTE]
>  Dinamik güncelleştirmeleri yalnızca bellekte oluşur ve yapılandırma dosyaları değişiklik neden değil.  
  
 RegularCalc ve roundingCalc Ekle aynı işlemlerini destekleyen, çıkarma, çarpma ve bölme; Ancak, roundingCalc döndürmeden önce hesaplamalarının yakın tamsayı değere yuvarlar. Bir yapılandırma dosyası, tüm iletileri regularCalc hizmete yönlendirmek için bu hizmeti yapılandırmak için kullanılır. Yönlendirme hizmeti başlatıldıktan sonra <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> roundingCalc hizmet iletileri yönlendirmek için hizmeti yeniden için kullanılır.  
  
### <a name="implement-initial-configuration"></a>Uygulama başlangıç yapılandırması  
  
1.  Temel yönlendirme hizmeti yapılandırma hizmeti tarafından sunulan hizmet uç noktalarına belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılan bir tek hizmet uç noktası tanımlar. Ayrıca, regularCalc iletileri göndermek için kullanılan bir istemci uç noktası tanımlar.  
  
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
  
2.  Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtre tanımlar. Bu örnekte, MatchAll filtre önceden tanımlanmış regularCalcEndpoint tüm iletileri yönlendirmek için kullanılır. Aşağıdaki örnek, filtre tablosu ve filtre tanımlar.  
  
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
  
3.  Filtre tablosunda bulunan filtreleriyle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile Filtresi tablosu ilişkilendirmelisiniz. Aşağıdaki örnek, hizmet uç noktası ile özellikle görüntüyle "filterTable1" gösterir.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Uygulama dinamik yapılandırma  
 Yönlendirme hizmeti, dinamik olarak yapılandırılmasını yalnızca yapılabilir kodda yeni oluşturarak <xref:System.ServiceModel.Routing.RoutingConfiguration> ve kullanarak <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmayı değiştirmek için.  Bu örnekte, yönlendirme hizmeti bir konsol uygulaması içinde kendi kendine büyük/küçük harf barındırılır. Uygulama başlatıldıktan sonra konsol penceresinden iletileri yönlendirilir hedef uç noktası yapılandırmak için 'Normal' veya 'yuvarlama' girerek yönlendirme yapılandırmasını değiştirebilirsiniz; 'Normal zaman' regularCalc girilen, aksi takdirde 'yuvarlarken' roundingCalc girilir.  
  
1.  Aşağıdaki yönlendirme hizmeti desteklemek için using deyimleri eklenmelidir.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2.  Aşağıdaki kod yönlendirme hizmeti bir konsol uygulaması olarak kendi kendine barındırmak için kullanılır. Bu yönlendirme kullanılarak uygulama yapılandırma dosyasında yer alan önceki adımda açıklanan Yapılandırma hizmetini başlatır. While döngü yönlendirme yapılandırmasını değiştirmek için kullanılan kod içerir.  
  
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
  
3.  Dinamik yönlendirme yapılandırmasını güncelleştirmek için yeni bir yönlendirme yapılandırması oluşturulması gerekir. Varolan yönlendirme yapılandırmasını tamamen yerini alacak şekilde bu tüm uç noktaları, filtreleri ve yeni yönlendirme yapılandırması için gerekli olan filtre tablolara içermesi gerekir. Yeni yönlendirme yapılandırmasını kullanmak için çağırmalıdır <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> ve yeni yapılandırmayı geçirin.  
  
     Aşağıdaki kodu ekleyin while Hizmeti'nin yapılandırılması izin vermek için önceden tanımlanmış döngü kullanıcı girişini temel alarak.  
  
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
    >  Sağlama yöntemini itibaren yeni RoutingConfiguration nesneleri sağlanabilir herhangi bir yere ServiceHost başvuru elde edebilirsiniz veya WCF genişletilebilirlik modeli yeni RoutingConfiguration RoutingExtension hizmet uzantısı'nda bulunan veya ServiceExtensions (başka bir ServiceExtension olduğu gibi). Bu şekilde RoutingConfiguration dinamik güncelleştirme bir örnek için bkz: [dinamik yeniden yapılandırma](../../../../docs/framework/wcf/samples/dynamic-reconfiguration.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte kullanılan konsol uygulaması tam bir listesi aşağıda verilmiştir.  
  
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
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma tam bir listesi verilmiştir Bu örnekte kullanılan dosya.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
