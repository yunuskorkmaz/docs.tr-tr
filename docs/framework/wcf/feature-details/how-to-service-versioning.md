---
title: 'Nasıl yapılır: Hizmet Sürümü Oluşturma'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: 5f79382eb121472ffa32d969cfaeee0e83d3375d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198403"
---
# <a name="how-to-service-versioning"></a>Nasıl yapılır: Hizmet Sürümü Oluşturma
Bu konuda aynı hizmetin farklı sürümlerine iletileri yönlendiren bir yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır. Bu örnekte, iki farklı sürümlerine bir hesap makinesi hizmet iletileri yönlendirilir `roundingCalc` (v1) ve `regularCalc` (v2). Hem uygulamalar aynı işlemleri desteği: Ancak, eski hizmet `roundingCalc`, sonuç döndürülmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır. Yeni kullanılıp kullanılmayacağını belirtmek bir istemci uygulaması erişebilmelidir `regularCalc` hizmeti.  
  
> [!WARNING]
>  Bir özel hizmet sürümünden bir ileti yönlendirmek için yönlendirme hizmeti ileti içeriğine göre ileti hedef belirlemek mümkün olması gerekir. Aşağıda gösterilen yöntemi, istemci, sürüm bilgileri bir ileti üst bilgisi ekleyerek belirtin. Ek veri iletmek istemcileri gerektirmeyen hizmet sürümü oluşturma yöntemleri vardır. Örneğin, bir ileti için en son yönlendirilebilir veya bir hizmet veya yönlendirici en uyumlu sürümü standart SOAP Zarfı parçası kullanabilir.  
  
 Her iki hizmet tarafından sunulan işlemleri şunlardır:  
  
-   Ekle  
  
-   Çıkarma  
  
-   Çarp  
  
-   Bölme  
  
 Her iki hizmet uygulamalarını aynı işlemleri işlemek ve dışında döndürmeleri veri temel olarak aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemek olanak tanımak için benzersiz değil İstek. Örneğin, eylem filtrelerini her iki hizmet için varsayılan Eylemler aynı olduğundan kullanılamaz.  
  
 Yönlendirici hizmetinin her sürüm için belirli bir uç noktada kullanıma veya hizmet sürümü belirten iletiyi için özel üstbilgi öğesi ekleme gibi çeşitli şekillerde çözülebilir.  Bu yaklaşımların her birinin benzersiz bir şekilde hizmetin belirli bir sürüme gelen iletileri yönlendirmek sağlar, ancak benzersiz ileti içeriğini kullanan istekler için farklı hizmet sürümleri arasında ayrım yapma, tercih edilen yöntemdir.  
  
 Bu örnekte istemci uygulaması için istek iletisi 'CalcVer' özel üst bilgi ekler. Bu üst bilgi iletisi için yönlendirileceğini hizmetinin sürümü belirten bir değer içerir. Değerini '1', '2' değerini regularCalc hizmeti çağrılırken, ileti roundingCalc hizmeti tarafından işlenen gerekir gösterir. Bu iletiyi hizmetin hangi sürümünün işleyecek doğrudan denetlemek istemci uygulaması sağlar.  Özel üst bilgi iletisi içinde yer alan bir değer olduğundan, her iki hizmeti sürümleri hedefleyen iletileri almak için bir uç nokta kullanabilirsiniz. Aşağıdaki kod, bu özel üstbilgi iletiye eklemek için istemci uygulamasında kullanılabilir:  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a>Uygulama hizmet sürümü oluşturma  
  
1.  Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktası belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılacak bir tek hizmet uç noktası tanımlar. Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar `roundingCalc` (v1) ve `regularCalc` (v2) Hizmetleri.  
  
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
  
2.  Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.  Bu örnekte, XPath filtresi, hangi sürümü için ileti yönlendirileceğini belirlemek için "CalcVer" özel üst bilgi değeri algılamak için kullanılır. Bir XPath filtresi "CalcVer" üst bilgi içermeyen iletilerini algılamak için de kullanılır. Aşağıdaki örnek, ad alanı tablosu ve gerekli filtreleri tanımlar.  
  
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
    > S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve ad alanını temsil eden `http://www.w3.org/2003/05/soap-envelope`.
  
3.  Her filtre bir istemci uç noktası ile ilişkilendirir filtre tablo tanımlayın. İleti "CalcVer" üst bilgi değeri 1 ile içeriyorsa regularCalc hizmetine gönderilir. Başlığı 2 değerini içeriyorsa, roundingCalc hizmetine gönderilir. Üst bilgi varsa, ileti için regularCalc yönlendirilir.  
  
     Aşağıdaki filtre tabloyu tanımlayan ve daha önce tanımlanan filtreler ekler.  
  
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
  
4.  Filtre tablosunda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz. Aşağıdaki örnek, ilişkilendirme gösterir `filterTable1` hizmet uç noktaları ile:  
  
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
 Yapılandırma dosyasının tam bir listesi verilmiştir.  
  
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
 İstemci uygulamasının tam bir listesi verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
