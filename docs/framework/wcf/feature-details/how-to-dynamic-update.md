---
title: 'Nasıl yapılır: Dinamik Güncelleştirme'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: 3c651bc4ff23b2534e81f190fc8b63771c7587d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911151"
---
# <a name="how-to-dynamic-update"></a>Nasıl yapılır: Dinamik Güncelleştirme
Bu konuda, yönlendirme yapılandırmasını oluşturmak ve dinamik olarak güncelleştirmek için gereken temel adımlar özetlenmektedir. Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından alınır ve tüm iletileri regularCalc Hesaplayıcı hizmetine yönlendirir; Ancak, bu daha sonra kaynak uç noktasını roundingCalc hizmeti değiştirmek için programlı olarak güncelleştirilir.  
  
> [!NOTE]
> Birçok uygulamada, yapılandırma tamamen dinamik olur ve varsayılan bir yapılandırmaya güvenmeyecektir; Ancak, bu konu başlığı altında, hizmet başlatıldığında varsayılan bir yapılandırma durumuna sahip olmak istenen bazı senaryolar vardır.  
  
> [!NOTE]
> Dinamik güncelleştirmeler yalnızca bellekte oluşur ve yapılandırma dosyalarının değiştirilmesine neden olmaz.  
  
 Hem regularCalc hem de roundingCalc, ekleme, çıkarma, çarpma ve bölme işlemlerini destekler; Ancak roundingCalc, döndürmeden önce tüm hesaplamaları en yakın tamsayı değerine yuvarlar. Bir yapılandırma dosyası, tüm iletileri regularCalc hizmetine yönlendirmek üzere hizmetini yapılandırmak için kullanılır. Yönlendirme hizmeti başlatıldıktan sonra, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> iletileri roundingcalc hizmetine yönlendirmek üzere hizmeti yeniden yapılandırmak için kullanılır.  
  
### <a name="implement-initial-configuration"></a>Ilk yapılandırmayı Uygula  
  
1. Hizmet tarafından sunulan hizmet uç noktalarını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun. Aşağıdaki örnek, ileti almak için kullanılacak tek bir hizmet uç noktasını tanımlar. Ayrıca, regularCalc 'e ileti göndermek için kullanılacak bir istemci uç noktası da tanımlar.  
  
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
  
2. İletileri hedef uç noktalara yönlendirmek için kullanılan filtreyi tanımlayın. Bu örnekte, tüm iletileri daha önce tanımlanan regularCalcEndpoint öğesine yönlendirmek için MatchAll filtresi kullanılır. Aşağıdaki örnekte Filter ve Filter tablosu tanımlanmaktadır.  
  
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
  
3. Gelen iletileri filtre tablosunda yer alan filtrelere karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir. Aşağıdaki örnek, "filterTable1" ın hizmet uç noktasıyla ilişkilendirilmesini gösterir.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Dinamik yapılandırmayı Uygula  
 Yönlendirme hizmetinin dinamik yapılandırması yalnızca yeni <xref:System.ServiceModel.Routing.RoutingConfiguration> bir oluşturma ve geçerli yapılandırmayı değiştirmek için kullanılarak <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> kod içinde gerçekleştirilebilir.  Bu örnekte, yönlendirme hizmeti bir konsol uygulaması içinde kendiliğinden barındırılır. Uygulama başladıktan sonra, iletilerin yönlendirildiği hedef uç noktasını yapılandırmak için konsol penceresine ' Regular ' veya ' yuvarla ' girerek yönlendirme yapılandırmasını değiştirebilirsiniz; ' Regular ' girildiğinde regularCalc, aksi takdirde, ' yuvarlama ' girildiğinde roundingCalc.  
  
1. Yönlendirme hizmetini desteklemek için aşağıdaki using deyimleri eklenmelidir.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Aşağıdaki kod, yönlendirme hizmetini bir konsol uygulaması olarak kendine barındırmak için kullanılır. Bu, uygulama yapılandırma dosyası içinde yer alan önceki adımda açıklanan yapılandırmayı kullanarak yönlendirme hizmetini başlatır. While döngüsü, yönlendirme yapılandırmasını değiştirmek için kullanılan kodu içerir.  
  
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
  
3. Yönlendirme yapılandırmasını dinamik olarak güncelleştirmek için yeni bir yönlendirme yapılandırmasının oluşturulması gerekir. Bu, mevcut yönlendirme yapılandırmasının tamamen yerini alacak şekilde, yeni yönlendirme yapılandırması için gereken tüm uç noktaları, filtreleri ve filtre tablolarını içermelidir. Yeni yönlendirme yapılandırmasını kullanmak için yeni yapılandırmayı çağırmanız <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> ve geçirmeniz gerekir.  
  
     Hizmetin kullanıcı girişine göre yeniden yapılandırılması için aşağıdaki kodu daha önce tanımlanan while döngüsüne ekleyin.  
  
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
    > Yeni bir RoutingConfiguration sağlamaya yönelik Yöntem RoutingExtension hizmeti uzantısında yer aldığı için, yeni RoutingConfiguration nesneleri, veya ServiceHost öğesine bir başvuru elde eden ya da alabileceği WCF genişletilebilirlik modeli içinde sağlanabilir ServiceExtensions (örneğin, başka bir ServiceExtension).
  
## <a name="example"></a>Örnek  
 Aşağıda, bu örnekte kullanılan konsol uygulamasının tamamen bir listesi verilmiştir.  
  
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
 Aşağıda, bu örnekte kullanılan yapılandırma dosyasının tamamen bir listesi verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
