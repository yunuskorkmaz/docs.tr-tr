---
title: 'Nasıl yapılır: Hata İşleme'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 3752e358230b76d8984fa8e6a2ded43ad0eb2c6c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334997"
---
# <a name="how-to-error-handling"></a>Nasıl yapılır: Hata İşleme
Bu konuda, hata işleme kullanan bir yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır. Bu örnekte, bir hedef uç noktasına iletileri yönlendirilir. Bir ağ veya iletişim ilgili bir hata nedeniyle bir ileti gönderilemezse (<xref:System.ServiceModel.CommunicationException>), ileti başka bir uç noktasına gönderilir.  
  
> [!NOTE]
>  Bir ağ hatası benzetimini yapmak için bu örnekte kullanılan hedef uç nokta adresi yanlış içerir. Bu uç nokta başarısız kıl hiçbir hizmet olarak yönlendirilmiş iletiler belirtilen adresinde dinlemede.  
  
> [!NOTE]
>  Bu konuda yer alan örnek zaman aşımı ayarlarını açıkça açıklanmamıştır, ancak bunlar dikkate hata işleme kullanırken atmanız gerekir. Hatalarla karşılaştı, istemci yanıt almadan önce karşılaştı, ek bir gecikme olur. Hata yönlendirme yapılacak bir yedekleme uç noktasına göndermesi dener hizmetinin, alınan olmasıdır. Zaman aşımı değerlerini ilişkili birincil ve yedek hedef uç noktaları büyük olduğundan, başarıyla gönderilmeden önce ileti yedekleme listesinde birden fazla uç nokta üzerinde başarısız olarak istemci kadar uzun bir gecikme.  
>   
>  Yönlendirme hizmeti, bir filtre ile ilişkili tüm uç noktalar için zaman aşımı değerini toplamına eşit en büyük gecikme karşılaşabilirsiniz olduğundan, buna göre istemcide beklenen zaman aşımını artırın öneririz.  
  
### <a name="implement-error-handling"></a>Hata işleme uygulama  
  
1. Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktası belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılan bir tek hizmet uç noktası tanımlar. Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination. DeadDestination uç nokta çalışan bir hizmete başvurmuyor ve bu uç noktaya iletileri gönderirken, bir ağ hatası benzetimini yapmak için kullanılan bir adres içeriyor.  
  
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
  
2. Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.  Bu örnekte, MatchAll filtre, yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3. Bir ileti bir ağ veya iletişim hatası durumunda birincil hedef uç noktasına gönderilirken gönderilen uç noktaları içeren yedekleme uç nokta listesi tanımlar. Aşağıdaki örnek, bir uç nokta içeren bir yedekleme listesini tanımlar; Ancak, birden fazla uç nokta yedekleme listesinde belirtilebilir.  
  
     Yedekleme listesinde birden fazla uç noktası, bir ağ içeriyorsa veya yönlendirme hizmeti iletişim hatası oluşur, listedeki ilk uç nokta ileti göndermeye çalışır. Bu uç noktaya gönderirken bir ağ veya iletişim hatası meydana gelirse, yönlendirme hizmeti listede yer alan sonraki uç nokta ileti göndermeye çalışır. Hizmet, ileti başarıyla gönderildi, tüm yedekleme uç noktaları bir ağ veya iletişimleri ile ilgili bir hata döndürür veya ileti gönderilir ve ağ dışı uç noktanın döndürdüğü kadar yedekleme uç noktası listesindeki her bir uç nokta için ileti gönderilirken devam eder iletişim ilgili olmayan bir hata oluştu.  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4. Filtre deadDestination uç nokta ve yedekleme uç nokta listesi ile ilişkilendirir filtre tablo tanımlayın.  Yönlendirme hizmeti, ilk filtresiyle ilişkili hedef uç nokta ileti göndermeye çalışır. DeadDestination çalışan bir hizmete başvurmuyor bir adres içerdiğinden, bu bir ağ hatasına neden olur. Yönlendirme hizmeti, ardından backupEndpointlist içinde belirtilen uç nokta ileti göndermeye çalışır.  
  
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
  
5. Filtre tablosunda yer alan filtre karşı gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz.  Aşağıdaki örnek, hizmet uç noktaları ile ilişkilendirmeyi "filterTable1" gösterir.  
  
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
 Yapılandırma dosyasının tam bir listesi verilmiştir.  
  
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
            <!-- Add an entrty that maps the MatchAllMessageFilter to the dead destination -->  
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
