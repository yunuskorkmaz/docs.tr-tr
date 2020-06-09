---
title: 'Nasıl yapılır: Hizmet Verilerini Bölümlendirme'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 3b2f86ee6a4dea25fb5c972d4cecb1b9ed411b29
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601198"
---
# <a name="how-to-service-data-partitioning"></a>Nasıl yapılır: Hizmet Verilerini Bölümlendirme
Bu konu başlığı altında, aynı hedef hizmetin birden çok örneğinde iletileri bölümlemek için gereken temel adımlar özetlenmektedir. Hizmet verileri bölümlendirme genellikle, daha iyi hizmet kalitesi sağlamak için veya belirli bir şekilde farklı müşterilerden gelen istekleri işleyebilmeniz gerektiğinde kullanılır. Örneğin, yüksek değerden veya "altın" müşterilerden gelen iletilerin, standart müşteriden gelen iletilerden daha yüksek bir önceliğe göre işlenmesi gerekebilir.  
  
 Bu örnekte, iletiler regularCalc hizmetinin iki örneklerinden birine yönlendirilir. Hizmetin her iki örneği de aynıdır; Ancak, Calculator1 uç noktası tarafından temsil edilen hizmet, yüksek değerli müşterilerden alınan iletileri işlediğinde, hesaplayıcı 2 uç noktası diğer müşterilerden gelen iletileri işler  
  
 İstemciden gönderilen iletinin, iletinin hangi hizmet örneğine yönlendirildiğini belirlemek için kullanılabilecek benzersiz verileri yok. Her bir istemcinin verileri belirli bir hedef hizmete yönlendirmesine izin vermek için, ileti almak için kullanılacak iki hizmet uç noktası uygulayacağız.  
  
> [!NOTE]
> Bu örnek, verileri bölümlemek için belirli uç noktaları kullandığında, bu da ileti içinde başlık veya gövde verileri gibi bilgiler kullanılarak da gerçekleştirilebilir.  
  
### <a name="implement-service-data-partitioning"></a>Hizmet veri bölümlendirme uygulama  
  
1. Hizmet tarafından sunulan hizmet uç noktalarını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun. Aşağıdaki örnek, ileti almak için kullanılacak iki uç nokta tanımlar. Ayrıca, regularCalc hizmeti örneklerine ileti göndermek için kullanılan istemci uç noktalarını tanımlar.  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
       </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
        <endpoint name="CalcEndpoint1"  
                  address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
  
        <endpoint name="CalcEndpoint2"  
                  address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                  binding="netTcpBinding"  
                  contract="*" />  
     </client>  
    ```  
  
2. İletileri hedef uç noktalara yönlendirmek için kullanılan filtreleri tanımlayın.  Bu örnek için, EndpointName filtresi, iletiyi hangi hizmet uç noktasının aldığını tespit etmek için kullanılır. Aşağıdaki örnek, gerekli Yönlendirme bölümünü ve filtreleri tanımlar.  
  
    ```xml  
    <filters>  
      <!--define the different message filters-->  
      <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
      <filter name="HighPriority" filterType="EndpointName"  
              filterData="calculator1Endpoint"/>  
      <filter name="NormalPriority" filterType="EndpointName"  
              filterData="calculator2Endpoint"/>  
    </filters>  
    ```  
  
3. Her bir filtreyi bir istemci uç noktasıyla ilişkilendiren filtre tablosunu tanımlayın. Bu örnekte ileti, aldığı belirli uç noktaya göre yönlendirilir. İleti yalnızca iki olası filtreden birini eşleştirebilir, ancak filtrelerin değerlendirileceği sırayı denetlemek için filtre önceliği kullanılmasına gerek yoktur.  
  
     Aşağıda, filtre tablosu tanımlanmaktadır ve daha önce tanımlanan filtreler eklenir.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. Gelen iletileri tabloda yer alan filtrelere karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir. Aşağıdaki örnek, "filterTable1" ın hizmet uç noktaları ile ilişkilendirilmesini gösterir:  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--create the endpoints for the calculator service-->  
        <endpoint address="calculator1"  
                  binding="wsHttpBinding"  
                  name="calculator1Endpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <endpoint address="calculator2"  
                  binding="wsHttpBinding"  
                  name="calculator2Endpoint"  
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
      <endpoint name="CalcEndpoint1"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="CalcEndpoint2"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
  
      <filters>  
        <!--define the different message filters-->  
        <!--define endpoint name filters looking for messages that show up on the virtual endpoints-->  
        <filter name="HighPriority" filterType="EndpointName"  
                filterData="calculator1Endpoint"/>  
        <filter name="NormalPriority" filterType="EndpointName"  
                filterData="calculator2Endpoint"/>  
      </filters>  
  
      <filterTables>  
        <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
          <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
        </filterTable>  
      </filterTables>  
  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Hizmetleri](../samples/routing-services.md)
