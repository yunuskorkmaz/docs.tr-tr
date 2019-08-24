---
title: 'Nasıl yapılır: Hizmet Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: 5ce9e7fc896f1ebc46dd25777fc629532339cbe2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988713"
---
# <a name="how-to-service-versioning"></a>Nasıl yapılır: Hizmet Sürümü Oluşturma
Bu konuda, aynı hizmetin farklı sürümlerine iletileri yönlendiren bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar özetlenmektedir. Bu örnekte, iletiler bir hesap makinesi hizmetinin `roundingCalc` (v1) ve `regularCalc` (v2) iki farklı sürümüne yönlendirilir. Her iki uygulama da aynı işlemleri destekler; Ancak eski hizmet `roundingCalc`, döndürmeden önce tüm hesaplamaları en yakın tamsayı değerine yuvarlar. İstemci uygulaması, yeni `regularCalc` hizmetin kullanılıp kullanılmayacağını belirtebilmelidir.  
  
> [!WARNING]
> Bir iletiyi belirli bir hizmet sürümüne yönlendirmek için, yönlendirme hizmeti ileti içeriğini temel alarak ileti hedefini belirleyebilmelidir. Aşağıda gösterilen yöntemde, istemci, bir ileti üstbilgisine bilgi ekleyerek sürümü belirler. Hizmet sürümü oluşturma, istemcilerin ek veri geçmesini gerektirmeyen yöntemler vardır. Örneğin, bir ileti bir hizmetin en son veya en uyumlu sürümüne yönlendirilebilir veya yönlendirici standart SOAP zarfının bir parçasını kullanabilir.  
  
 Her iki hizmet tarafından kullanıma sunulan işlemler şunlardır:  
  
- Ekle  
  
- Çıkarma  
  
- Bilirsiniz  
  
- Sayısına  
  
 Her iki hizmet uygulaması da aynı işlemleri yaptığından ve temelde getirdikleri verilerden farklı olduklarından, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, bu işlemin nasıl yönlendirildiğini belirlemenizi sağlayacak kadar benzersiz değildir. isteyen. Örneğin, her iki hizmet için de varsayılan eylemler aynı olduğundan eylem filtreleri kullanılamaz.  
  
 Bu, hizmetin her bir sürümü için yönlendiricide belirli bir uç noktayı açığa çıkarmak veya hizmet sürümünü göstermek üzere iletiye özel bir üst bilgi öğesi eklemek gibi çeşitli yollarla çözülebilir.  Bu yaklaşımlardan her biri, gelen iletileri hizmetin belirli bir sürümüne benzersiz bir şekilde yönlendirmenize olanak tanır, ancak benzersiz ileti içeriğini kullanmak, farklı hizmet sürümlerine yönelik istekler arasında ayrım yapmak için tercih edilen yöntemdir.  
  
 Bu örnekte, istemci uygulaması ' CalcVer ' özel üstbilgisini istek iletisine ekler. Bu üst bilgi, iletinin yönlendirileceği hizmetin sürümünü belirten bir değer içerir. ' 1 ' değeri, iletinin roundingCalc hizmeti tarafından işlenmesi gerektiğini gösterir, ancak bir ' 2 ' değeri regularCalc hizmetini gösterir. Bu, istemci uygulamanın hangi hizmetin hizmet sürümünün iletiyi işleyeceğini doğrudan denetlemesini sağlar.  Özel üstbilgi ileti içinde yer alan bir değer olduğundan, hizmetin her iki sürümüne de yönelik iletileri almak için bir uç nokta kullanabilirsiniz. Aşağıdaki kod, bu özel üstbilgiyi iletiye eklemek için istemci uygulamasında kullanılabilir:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Hizmet sürümü oluşturmayı Uygula  
  
1. Hizmet tarafından açığa çıkarılan hizmet uç noktasını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun. Aşağıdaki örnek, ileti almak için kullanılacak tek bir hizmet uç noktasını tanımlar. Ayrıca, `roundingCalc` (v1) `regularCalc` ve (v2) hizmetlerine ileti göndermek için kullanılacak istemci uç noktalarını tanımlar.  
  
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
  
2. İletileri hedef uç noktalara yönlendirmek için kullanılan filtreleri tanımlayın.  Bu örnek için XPath filtresi, iletinin hangi sürüme yönlendirildiğini belirlemek için "CalcVer" özel üst bilgisinin değerini algılamak için kullanılır. XPath filtresi, "CalcVer" üstbilgisini içermeyen iletileri algılamak için de kullanılır. Aşağıdaki örnekte gerekli filtreler ve ad alanı tablosu tanımlanmaktadır.  
  
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
    > S12 ad alanı ön eki, ad alanı tablosunda varsayılan olarak tanımlanır ve ad alanını `http://www.w3.org/2003/05/soap-envelope`temsil eder.
  
3. Her bir filtreyi bir istemci uç noktasıyla ilişkilendiren filtre tablosunu tanımlayın. İleti, değeri 1 olan "CalcVer" üstbilgisini içeriyorsa, regularCalc hizmetine gönderilir. Üst bilgi 2 değeri içeriyorsa, roundingCalc hizmetine gönderilir. Üst bilgi yoksa, ileti regularCalc yönlendirilir.  
  
     Aşağıda, filtre tablosu tanımlanmaktadır ve daha önce tanımlanan filtreler eklenir.  
  
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
  
4. Gelen iletileri filtre tablosunda yer alan filtrelere karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir. Aşağıdaki örnek, hizmet uç `filterTable1` noktaları ile ilişkilendirme gösterir:  
  
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
 Yapılandırma dosyasının tüm listesi aşağıda verilmiştir.  
  
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
 Aşağıda, istemci uygulamasının tamamen bir listesi verilmiştir.  
  
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
