---
title: 'Nasıl yapılır: Hizmet Verilerini Bölümlendirme'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: c5cfd56943c97b70ef12276f1bae47fa870366a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150104"
---
# <a name="how-to-service-data-partitioning"></a>Nasıl yapılır: Hizmet Verilerini Bölümlendirme
Bu konuda, birden çok hedef hizmetin aynı örneğine bölüm iletileri için gerekli temel adımlar açıklanmaktadır. Hizmet verilerini bölümlendirme, genellikle daha iyi hizmet kalitesini sağlamak için bir hizmeti ölçeklendirmek gerektiğinde veya farklı müşterilerden gelen istekleri belirli bir şekilde işlemek üzere gerektiğinde kullanılır. Örneğin, yüksek bir değer veya "Altın" müşteriler gelen iletileri, standart bir müşteri iletilerden daha yüksek bir önceliğe işlenecek gerekebilir.  
  
 Bu örnekte, iletilerin regularCalc hizmetin iki örneği birine yönlendirilir. Her iki hizmetin örneklerini aynıdır; ancak yüksek değerli müşterilerden hesaplayıcı 2 uç nokta calculator1 uç nokta işlemleri iletiler tarafından temsil edilen hizmet diğer müşterilerden gelen iletileri işleme alınan  
  
 İstemciden gönderilen ileti için ileti yönlendirileceğini hangi hizmet örneğini tanımlamak için kullanılan herhangi bir benzersiz veri yok. Her bir istemciye belirli hedef hizmet için rota verilerini izin vermek için ileti almak için kullanılacak olan iki hizmet uç noktaları uygular.  
  
> [!NOTE]
>  Bu örnek verileri bölümlemek için özel uç noktaları kullanırken, bu da üst bilgi veya gövdesinde veri gibi ileti kendisi içinde yer alan bilgileri kullanarak sağlayabilirsiniz.  
  
### <a name="implement-service-data-partitioning"></a>Uygulama hizmeti veri bölümleme  
  
1.  Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktaları belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılan iki uç nokta tanımlar. Ayrıca, regularCalc hizmet örnekleri için ileti göndermek için kullanılan istemci uç noktalarını tanımlar.  
  
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
  
2.  Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.  Bu örnekte, Uçnoktaadı filtre, hangi hizmet uç noktası iletisi aldı belirlemek için kullanılır. Aşağıdaki örnek, gerekli yönlendirme bölüm ve filtreleri tanımlar.  
  
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
  
3.  Her filtre bir istemci uç noktası ile ilişkilendirir filtre tablo tanımlayın. Bu örnekte, ileti üzerinde alındı belirli bir uç göre yönlendirilir. İletinin yalnızca iki olası filtrelerden birini eşleşebilir olduğundan, hangi filtrelerde değerlendirilir sırasını denetlemek için filtre önceliği kullanma gerek yoktur.  
  
     Aşağıdaki filtre tabloyu tanımlayan ve daha önce tanımlanan filtreler ekler.  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  Tabloda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz. Aşağıdaki örnek, hizmet uç noktaları ile ilişkilendirmeyi "filterTable1" gösterir:  
  
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

- [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
