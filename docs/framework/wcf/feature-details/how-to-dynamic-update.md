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
# <a name="how-to-dynamic-update"></a>Nasıl yapılır: Dinamik Güncelleştirme
Bu konuda, oluşturmak ve dinamik yönlendirme yapılandırmasını güncelleştirmek için gerekli temel adımlar açıklanmaktadır. Bu örnekte, ilk yönlendirme yapılandırması yapılandırma dosyasından alınır ve tüm iletileri regularCalc hesaplayıcı hizmete yönlendirir; Ancak, bu program aracılığıyla roundingCalc service hedef uç noktası değiştirmek üzere güncelleştirilir.  
  
> [!NOTE]
>  Birçok uygulama, yapılandırma tamamen dinamik ve varsayılan yapılandırma üzerinde bağımlı kalmayacak; Ancak, hizmeti başladığında, varsayılan yapılandırma durumu etmesi olduğu gibi bu konuda, bir bazı senaryolar vardır.  
  
> [!NOTE]
>  Dinamik güncelleştirme yalnızca bellekte oluşur ve yapılandırma dosyalarının değişiklik neden.  
  
 RegularCalc hem roundingCalc Ekle aynı işlemleri destekleyen, çıkarma, çarpma ve bölme; Ancak, roundingCalc döndürmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır. Bir yapılandırma dosyası, hizmeti tüm iletileri regularCalc hizmetine yönlendirecek şekilde yapılandırmak için kullanılır. Yönlendirme hizmeti başlatıldıktan sonra <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> roundingCalc hizmetine iletileri yönlendirmek için hizmeti yeniden yapılandırmak için kullanılır.  
  
### <a name="implement-initial-configuration"></a>Başlangıç yapılandırmasını Uygula  
  
1. Temel yönlendirme hizmeti yapılandırması hizmet tarafından sunulan hizmet uç noktaları belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılacak bir tek hizmet uç noktası tanımlar. Ayrıca, regularCalc için ileti göndermek için kullanılan istemci uç noktası tanımlar.  
  
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
  
2. Hedef Uç noktalara iletileri yönlendirmek için kullanılan bir filtre tanımlar. Bu örnekte, MatchAll filtre önceden tanımlanmış regularCalcEndpoint tüm iletileri yönlendirmek için kullanılır. Aşağıdaki örnek, filtreleme tablosu ve filtre tanımlar.  
  
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
  
3. Filtre tablosunda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz. Aşağıdaki örnek, hizmet uç noktası ile ilişkilendirmeyi "filterTable1" gösterir.  
  
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
  
## <a name="implement-dynamic-configuration"></a>Dinamik uygulama yapılandırması  
 Dinamik yönlendirme hizmeti yapılandırması yalnızca gerçekleştirilebilecek kod içinde yeni bir oluşturarak <xref:System.ServiceModel.Routing.RoutingConfiguration> ve kullanarak <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> geçerli yapılandırmasını değiştirmek için.  Bu örnekte, yönlendirme hizmeti bir konsol uygulaması içinde şirket içinde barındırılan. Uygulama başlatıldıktan sonra konsol penceresinde iletileri yönlendirilir hedef uç noktasını yapılandırmak için 'Normal' veya 'yuvarlama' girerek yönlendirme yapılandırmayı değiştirebilirsiniz; 'Normal'olduğunda ' regularCalc girilir, aksi takdirde 'yuvarlarken' roundingCalc girilir.  
  
1. Aşağıdaki yönlendirme hizmetini desteklemek için using deyimlerini eklenmelidir.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. Aşağıdaki kod, yönlendirme hizmeti bir konsol uygulaması olarak kendi kendine barındırmak için kullanılır. Bu yönlendirme kullanarak uygulama yapılandırma dosyası içinde yer alan önceki adımda açıklanan Yapılandırma hizmetini başlatır. While döngüsü yönlendirme yapılandırmasını değiştirmek için kullanılan kod içerir.  
  
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
  
3. Dinamik yönlendirme yapılandırmasını güncelleştirmek için yeni bir yönlendirme yapılandırması oluşturulması gerekir. Mevcut yönlendirme yapılandırmasını tamamen değiştirecek şekilde bu tüm uç noktaları, filtreler ve yeni yönlendirme yapılandırma için gerekli olan filtre tabloları içermelidir. Yeni yönlendirme yapılandırması kullanmak için çağırmalıdır <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> ve yeni yapılandırma geçişi.  
  
     Aşağıdaki kodu ekleyin while döngüsü hizmetinin yapılandırılması izin vermek için önceden tanımlanmış kullanıcı girişini temel alarak.  
  
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
    > Sağlama yöntemini beri yeni RoutingConfiguration RoutingExtension hizmet uzantısı, yeni RoutingConfiguration nesneleri sağlanabilir herhangi bir ServiceHost başvuru elde edebilirsiniz veya WCF genişletilebilirlik modeli içinde bulunan veya ServiceExtensions (başka bir ServiceExtension gibi).
  
## <a name="example"></a>Örnek  
 Bu örnekte kullanılan konsol uygulamasının tam listesi verilmiştir.  
  
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
 Yapılandırmayı tam bir listesi aşağıdadır Bu örnekte kullanılan dosya.  
  
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
