---
title: 'Nasıl yapılır: Hata İşleme'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3b8e48a74ff7671b942b5499fb3a0b5d0f389d61
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834709"
---
# <a name="how-to-error-handling"></a>Nasıl yapılır: Hata İşleme

Bu konuda, hata işleme kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar özetlenmektedir. Bu örnekte, iletiler bir hedef uç noktaya yönlendirilir. Bir ileti ağ veya iletişimle ilgili bir başarısızlık (<xref:System.ServiceModel.CommunicationException>) nedeniyle iletilemez, ileti alternatif bir uç noktaya yeniden gönderilir.

> [!NOTE]
> Bir ağ hatasının benzetimini yapmak için, bu örnekte kullanılan hedef uç noktası yanlış bir adres içeriyor. Belirtilen adreste hiçbir hizmet dinlemede olmadığından, bu uç noktaya yönlendirilen iletiler başarısız olur.

> [!NOTE]
> Bu konuda yer alan örnek, zaman aşımı ayarlarını açıkça ele almadığı sürece, hata işleme kullanırken bunları dikkate almanız gerekir. Hatalarla karşılaşıldığında, istemci yanıt almadan önce ek bir gecikme ile karşılaşıldı. Bunun nedeni, hatanın yönlendirme hizmetinde alınması ve daha sonra iletiyi bir yedekleme uç noktasına göndermenizi dener. Birincil ve yedek hedef uç noktalarıyla ilişkili zaman aşımı değerleri büyükse, ileti başarıyla gönderilmeden önce yedekleme listesindeki birden fazla uç nokta üzerinde hata verdiğinde, istemci uzun bir gecikmeyle karşılaşabilir.
>
> Yönlendirme hizmeti bir filtreyle ilişkili tüm uç noktalar için zaman aşımı değerinin toplamına eşit olan en büyük gecikmeyle karşılaştırabileceğinizden, istemcide beklenen zaman aşımını de artırmanız önerilir.

### <a name="implement-error-handling"></a>Hata Işlemeyi Uygula

1. Hizmet tarafından açığa çıkarılan hizmet uç noktasını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun. Aşağıdaki örnek, ileti almak için kullanılan tek bir hizmet uç noktasını tanımlar. Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination. DeadDestination uç noktası, çalışan bir hizmete başvurmayan ve bu uç noktaya ileti gönderilirken bir ağ başarısızlığının benzetimini yapmak için kullanılan bir adres içeriyor.

    ```xml
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>

    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    ```

2. İletileri hedef uç noktalara yönlendirmek için kullanılan filtreleri tanımlayın.  Bu örnekte, bir MatchAll filtresi, yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. Bir iletinin bir ağ olayında gönderildiği bitiş noktalarını veya birincil hedef uç noktasına gönderilirken iletişim hatasını içeren yedekleme uç noktası listesini tanımlayın. Aşağıdaki örnek bir uç nokta içeren bir yedekleme listesi tanımlar; Ancak, bir yedekleme listesinde birden fazla uç nokta belirtilebilir.

     Yedekleme listesi birden çok uç nokta içeriyorsa, bir ağ veya iletişim hatası oluştuğunda, ileti listedeki ilk uç noktaya gönderilmeye çalışır. Bu uç noktaya gönderilirken bir ağ veya iletişim hatası oluşursa, yönlendirme hizmeti iletiyi listede yer alan bir sonraki uç noktaya göndermeye çalışır. Hizmet, ileti başarıyla gönderilene kadar yedekleme uç noktası listesindeki her bir uç noktaya iletiyi göndermeye devam eder, tüm yedekleme uç noktaları ağ veya iletişimlerle ilgili bir hata döndürmüyor, ya da ileti gönderilir ve uç nokta ağ olmayan bir değer döndürür. iletişimlerle ilgili olmayan hata.

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. Filtreyi deadDestination bitiş noktasıyla ve yedekleme uç noktası listesiyle ilişkilendiren filtre tablosunu tanımlayın.  Yönlendirme hizmeti ilk olarak iletiyi filtreyle ilişkili hedef uç noktaya gönderilmeye çalışır. DeadDestination, çalışan bir hizmete başvurmayan bir adres içerdiğinden, bu durum Ağ hatasına neden olur. Yönlendirme hizmeti daha sonra iletiyi backupEndpointList öğesinde belirtilen uç noktaya gönderme girişiminde bulunur.

    ```xml
    <filterTables>
            <!-- Set up the Routing Service's Message Filter Table -->
            <filterTable name="filterTable1">
                <!-- Add an entity that maps the MatchAllMessageFilter to the dead destination -->
                <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
                <!-- Listed in the backupEndpointList -->
                <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
            </filterTable>
          </filterTables>
    ```

5. Gelen iletileri filtre tablosunda bulunan filtreye karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir.  Aşağıdaki örnek, "filterTable1" ın hizmet uç noktalarıyla ilişkilendirilmesini gösterir.

    ```xml
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>Örnek

Yapılandırma dosyasının tüm listesi aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!-- Copyright (c) Microsoft Corporation.  All Rights Reserved. -->
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="routingConfiguration"
               name="System.ServiceModel.Routing.RoutingService">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost/routingservice/" />
          </baseAddresses>
        </host>
        <!-- Create the Routing Service endpoint -->
        <endpoint address="router"
                  binding="basicHttpBinding"
                  name="RoutingServiceEndpoint"
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <!-- Set up the Routing Behavior -->
        <behavior name="routingConfiguration">
          <routing filterTableName="filterTable1" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <!-- Create the destination endpoints that we want to send to -->
    <client>
      <!-- Create a dummy endpoint that we know will be down -->
      <endpoint name="deadDestination"
                address="net.tcp://localhost:9090/servicemodelsamples/fakeDestination"
                binding="netTcpBinding"
                contract="*" />

      <!-- Now create the real service endpoint -->
      <endpoint name="realDestination"
                address="net.tcp://localhost:8080/servicemodelsamples/service"
                binding="netTcpBinding"
                contract="*" />
    </client>
    <routing>
      <filters>
        <!-- Create a MatchAll filter which will catch all messages -->
        <filter name="MatchAllFilter1" filterType="MatchAll" />
      </filters>
      <filterTables>
        <!-- Set up the Routing Service's Message Filter Table -->
        <filterTable name="filterTable1">
            <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
            <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
            <!-- Listed in the backupEndpointList -->
            <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
        </filterTable>
      </filterTables>
      <!-- Create the backup endpoint list -->
      <backupLists>
        <backupList name="backupEndpointList">
            <add endpointName="realDestination" />
        </backupList>
      </backupLists>
      </routing>
  </system.serviceModel>
</configuration>
```
