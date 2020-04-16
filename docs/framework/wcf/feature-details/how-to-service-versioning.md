---
title: 'Nasıl yapılır: Hizmet Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: f1178a0bedfe8665d7b3ec463e99183809538c28
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464123"
---
# <a name="how-to-service-versioning"></a>Nasıl yapılır: Hizmet Sürümü Oluşturma
Bu konu, iletileri aynı hizmetin farklı sürümlerine yollayan bir yönlendirme yapılandırması oluşturmak için gereken temel adımları özetler. Bu örnekte, iletiler bir hesap makinesi hizmetinin `roundingCalc` (v1) `regularCalc` ve (v2) iki farklı sürümüne yönlendirilir. Her iki uygulama da aynı işlemleri destekler; ancak eski hizmet, `roundingCalc`döndürmeden önce tüm hesaplamaları en yakın tümsavar değerine yuvarlar. İstemci uygulaması, yeni `regularCalc` hizmeti kullanıp kullanmayacağını belirtebilmeli.  
  
> [!WARNING]
> İletiyi belirli bir hizmet sürümüne yönlendirmek için Yönlendirme Hizmeti'nin ileti içeriğini temel alan ileti hedefini belirleyebilmesi gerekir. Aşağıda gösterilen yöntemde, istemci bir ileti üstbilgisine bilgi ekleyerek sürümü belirtir. İstemcilerin ek veri geçirmesini gerektirmeyen hizmet sürüm yöntemleri vardır. Örneğin, bir ileti bir hizmetin en son veya en uyumlu sürümüne yönlendirilebilir veya yönlendirici standart SOAP zarfının bir parçasını kullanabilir.  
  
 Her iki hizmettarafından ortaya çıkarılan işlemler şunlardır:  
  
- Ekle  
  
- Çıkar  
  
- Çarp  
  
- Böl  
  
 Her iki hizmet uygulaması da aynı işlemleri işlediği nden ve döndükleri veriler dışında temelde aynı olduğundan, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, isteği nasıl yönlendireceklerini belirlemenize izin verecek kadar benzersiz değildir. Örneğin, her iki hizmet için varsayılan eylemler aynı olduğundan Eylem filtreleri kullanılamaz.  
  
 Bu, hizmetin her sürümü için yönlendiricide belirli bir bitiş noktası ortaya çıkarmak veya iletiye hizmet sürümünü göstermek için özel bir üstbilgi öğesi eklemek gibi çeşitli yollarla çözülebilir.  Bu yaklaşımların her biri, gelen iletileri hizmetin belirli bir sürümüne benzersiz bir şekilde yönlendirmenize olanak tanır, ancak benzersiz ileti içeriğini kullanmak, farklı hizmet sürümleri istekleri ni ayırt etmek için tercih edilen yöntemdir.  
  
 Bu örnekte, istemci uygulaması istek iletisine 'CalcVer' özel üstbilgisini ekler. Bu üstbilgi, iletinin yönlendirilmesi gereken hizmetin sürümünü gösteren bir değer içerir. '1' değeri iletinin yuvarlamaCalc hizmeti tarafından işlenmesi gerektiğini gösterirken, '2' değeri düzenli Calc hizmetini gösterir. Bu, istemci uygulamasının iletiyi hangi hizmet sürümünde işleyecek lerini doğrudan denetlemesine olanak tanır.  Özel üstbilgi iletide bulunan bir değer olduğundan, hizmetin her iki sürümü için de mukadder iletileri almak için bir bitiş noktası kullanabilirsiniz. İletiye bu özel üstbilgi eklemek için istemci uygulamasında aşağıdaki kod kullanılabilir:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Hizmet Sürümünü Uygula  
  
1. Hizmettarafından açığa çıkarılan hizmet bitiş noktasını belirterek temel Yönlendirme Hizmeti yapılandırmasını oluşturun. Aşağıdaki örnek, ileti leri almak için kullanılacak tek bir hizmet bitiş noktasını tanımlar. `roundingCalc` Ayrıca(v1) ve (v2) hizmetlerine ileti göndermek için kullanılacak istemci `regularCalc` uç noktalarını tanımlar.  
  
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
  
2. İletileri hedef uç noktalarına yönlendirmek için kullanılan filtreleri tanımlayın.  Bu örnekte, XPath filtresi, iletinin hangi sürüme yönlendirilmesi gerektiğini belirlemek için "CalcVer" özel üstbilginin değerini algılamak için kullanılır. XPath filtresi, "CalcVer" üstbilgisini içermeyen iletileri algılamak için de kullanılır. Aşağıdaki örnekte gerekli filtreler ve ad alanı tablosu tanımlanır.  
  
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
    </filters>
    ```  
  
    > [!NOTE]
    > s12 ad alanı öneki, ad alanı tablosunda varsayılan olarak `http://www.w3.org/2003/05/soap-envelope`tanımlanır ve ad alanını temsil eder.
  
3. Her filtreyi istemci bitiş noktasıyla ilişkilendiren filtre tablosunu tanımlayın. İleti 1 değeri olan "CalcVer" üstbilgisini içeriyorsa, normal Calc hizmetine gönderilir. Üstbilgi 2 değeri içeriyorsa, yuvarlamaCalc hizmetine gönderilir. Üstbilgi yoksa, ileti normal Calc'ye yönlendirilir.  
  
     Aşağıdaki filtre tablosunu tanımlar ve daha önce tanımlanan filtreleri ekler.  
  
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
  
4. Gelen iletileri filtre tablosunda bulunan filtrelere göre değerlendirmek için yönlendirme davranışını kullanarak filtre tablosunu hizmet bitiş noktalarıyla ilişkilendirmeniz gerekir. Aşağıdaki örnek, hizmet bitiş `filterTable1` noktalarıyla ilişkilendirme olduğunu gösterir:  
  
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
  
## <a name="example"></a>Örnek  
 Aşağıda yapılandırma dosyasının tam listesi veremivettir.  
  
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
  
## <a name="example"></a>Örnek  
 Aşağıda istemci uygulamasının tam bir listesi vetir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
