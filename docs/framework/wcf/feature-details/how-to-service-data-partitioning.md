---
title: "Nasıl yapılır: Hizmet Verilerini Bölümlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6a3f95f2ecea342072de010a6cee51069f755fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-service-data-partitioning"></a>Nasıl yapılır: Hizmet Verilerini Bölümlendirme
Bu konu, birden çok örneğini aynı hedef hizmeti arasında bölüm iletileri için gereken temel adımlarda özetler. Hizmet verilerini bölümlendirme, genellikle daha iyi hizmet kalitesi sağlamak amacıyla bir hizmeti ölçeklendirmek gerektiğinde veya farklı müşterilerden gelen istekleri belirli bir şekilde işlemek üzere gerektiğinde kullanılır. Örneğin, yüksek bir değer veya "Altın" müşterilerden iletileri standart müşteri iletilerden daha yüksek bir öncelik işlenecek gerekebilir.  
  
 Bu örnekte, iletilerin regularCalc hizmetin iki örneğini birine yönlendirilir. Her iki hizmet örneklerini aynıdır; ancak calculator1 uç nokta işlemleri iletiler tarafından temsil edilen hizmet yüksek değerli müşterilerden hesaplayıcı 2 bitiş noktası diğer müşterilerden gelen iletileri işleme alınan  
  
 İstemciden gönderilen ileti için ileti yönlendirileceğini hangi hizmet örneğine tanımlamak için kullanılan herhangi bir benzersiz veri yok. Belirli bir hedef hizmet için rota verilerini her bir istemciye izin vermek için iletileri almak için kullanılan iki hizmet uç noktaları gerçekleştireceksiniz.  
  
> [!NOTE]
>  Bu örnek bölüm verilere özel uç noktaları kullanırken, bu da üstbilgi veya gövde verileri gibi ileti kendi içinde yer alan bilgileri kullanarak bunu sağlayabilirsiniz.  
  
### <a name="implement-service-data-partitioning"></a>Uygulama hizmet verilerini bölümlendirme  
  
1.  Temel yönlendirme hizmeti yapılandırma hizmeti tarafından sunulan hizmet uç noktalarına belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılan iki uç nokta tanımlar. Ayrıca, regularCalc hizmet örneklerine ileti göndermek için kullanılan istemci uç noktalarını tanımlar.  
  
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
  
2.  Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtrelerini tanımlayın.  Bu örnekte, EndpointName filtresi, hangi hizmet uç noktası iletisi aldı belirlemek için kullanılır. Aşağıdaki örnek, filtreleri ve gerekli yönlendirme bölüm tanımlar.  
  
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
  
3.  Her filtre bir istemci uç noktası ile ilişkilendirir Filtresi tablosu tanımlayın. Bu örnekte, ileti üzerinden alındı belirli bir uç göre yönlendirilir. İletinin yalnızca iki olası filtrelerden birini eşleştirebilirsiniz olduğundan, hangi filtreleri değerlendirilir siparişe denetlemek için filtre öncelik kullanma gerek yoktur.  
  
     Aşağıdaki filtre tablosunda tanımlar ve daha önce tanımlanan filtreler ekler.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  Tabloda bulunan filtreleriyle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile Filtresi tablosu ilişkilendirmelisiniz. Aşağıdaki örnek, hizmet uç noktaları ile özellikle görüntüyle "filterTable1" gösterir:  
  
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
 Yapılandırma dosyası tam bir listesi verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
