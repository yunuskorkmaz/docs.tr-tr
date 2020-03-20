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
# <a name="how-to-dynamic-update"></a>Nasıl yapılır: Dinamik Güncelleme
Bu konu, yönlendirme yapılandırmasını oluşturmak ve dinamik olarak güncelleştirmek için gereken temel adımları özetler. Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından elde edilir ve tüm iletileri normal Calc hesap makinesi hizmetine yönlendirir; ancak, daha sonra hedef bitiş noktası yuvarlamaCalc hizmeti değiştirmek için programlı olarak güncelleştirilir.  
  
> [!NOTE]
> Birçok uygulamada, yapılandırma tamamen dinamik olur ve varsayılan yapılandırmaya güvenmez; ancak, hizmet başlatıldığında varsayılan yapılandırma durumu olması nın arzu edildiği bu konudaki gibi bazı senaryolar vardır.  
  
> [!NOTE]
> Dinamik güncelleştirmeler yalnızca bellekte gerçekleşir ve yapılandırma dosyalarının değiştirilmesine neden olmaz.  
  
 Hem regularCalc hem de roundingCalc aynı ekleme, çıkarma, çarpma ve bölme işlemlerini destekler; ancak, yuvarlamaCalc dönmeden önce tüm hesaplamaları en yakın tümsakaradeğere yuvarlar. Tüm iletileri normal Calc hizmetine yönlendirecek şekilde hizmeti yapılandırmak için bir yapılandırma dosyası kullanılır. Yönlendirme Hizmeti başlatıldıktan sonra, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> iletileri yuvarlama Calc hizmetine yönlendirmek için hizmeti yeniden yapılandırmak için kullanılır.  
  
### <a name="implement-initial-configuration"></a>İlk Yapılandırmayı Uygula  
  
1. Hizmettarafından açığa çıkarılan hizmet bitiş noktalarını belirterek temel Yönlendirme Hizmeti Yapılandırmasını oluşturun. Aşağıdaki örnek, ileti leri almak için kullanılacak tek bir hizmet bitiş noktasını tanımlar. Ayrıca, düzenli Calc'ye ileti göndermek için kullanılacak bir istemci bitiş noktası tanımlar.  
  
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
  
2. İletileri hedef uç noktalarına yönlendirmek için kullanılan filtreyi tanımlayın. Bu örnekte, MatchAll filtresi tüm iletileri daha önce tanımlanan calcEndpoint'e yönlendirmek için kullanılır. Aşağıdaki örnekte filtre ve filtre tablosu tanımlanır.  
  
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
  
3. Gelen iletileri filtre tablosunda bulunan filtrelere göre değerlendirmek için yönlendirme davranışını kullanarak filtre tablosunu hizmet bitiş noktalarıyla ilişkilendirmeniz gerekir. Aşağıdaki örnekte, "filterTable1" ile hizmet bitiş noktası ilişkilendirme gösterilmektedir.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Dinamik Yapılandırma uygulayın  
 Yönlendirme Hizmetinin dinamik yapılandırması yalnızca yeni <xref:System.ServiceModel.Routing.RoutingConfiguration> bir oluşturma ve <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmayı değiştirmek için kullanılarak kod olarak gerçekleştirilebilir.  Bu örnekte, Yönlendirme Hizmeti bir konsol uygulaması içinde kendi kendine barındırılan. Uygulama başladıktan sonra, iletilerin yönlendirildiği hedef bitiş noktasını yapılandırmak için konsol penceresine 'normal' veya 'yuvarlama' girerek yönlendirme yapılandırmasını değiştirebilirsiniz; regularCalc 'normal' girildiğinde, aksi takdirde 'yuvarlama' girildiğinde Calc yuvarlama.  
  
1. Yönlendirme Hizmetini desteklemek için aşağıdaki ifadeler eklenmelidir.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Aşağıdaki kod, Yönlendirme Hizmetini konsol uygulaması olarak kendi kendine barındırmak için kullanılır. Bu, uygulama yapılandırma dosyasında bulunan önceki adımda açıklanan yapılandırmayı kullanarak Yönlendirme Hizmeti'ni başlatır. While döngüsü yönlendirme yapılandırmasını değiştirmek için kullanılan kodu içerir.  
  
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
  
3. Yönlendirme yapılandırmasını dinamik olarak güncelleştirmek için yeni bir yönlendirme yapılandırması oluşturulması gerekir. Bu, varolan yönlendirme yapılandırmasının tamamen yerini alacağı için, yeni yönlendirme yapılandırması için gereken tüm uç noktaları, filtreleri ve filtre tablolarını içermelidir. Yeni yönlendirme yapılandırmasını kullanmak için, yeni <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yapılandırmayı çağırmanız ve geçmeniz gerekir.  
  
     Hizmetin kullanıcı girişine göre yeniden yapılandırılabilmesi için daha önce tanımlanan while döngüsüne aşağıdaki kodu ekleyin.  
  
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
    > Yeni bir YönlendirmeYapılandırması sağlama yöntemi RoutingExtension hizmet uzantısında bulunduğundan, Yeni RoutingConfiguration nesneleri WCF genişletilebilirlik modelinde ServiceHost veya ServiceExtensions (başka bir ServiceExtension gibi).
  
## <a name="example"></a>Örnek  

Aşağıdaki, bu örnekte kullanılan konsol uygulamasının tam bir listesidir:
  
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
  
## <a name="example"></a>Örnek  

Aşağıda, bu örnekte kullanılan yapılandırma dosyasının tam listesi verilmiştir:
  
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

- [Yönlendirme Hizmetleri](../samples/routing-services.md)
