---
title: 'Nasıl yapılır: Hata İşleme'
ms.date: 03/30/2017
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
ms.openlocfilehash: 7b173997eb53f8cf156ccb14083885a199dc8921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493611"
---
# <a name="how-to-error-handling"></a>Nasıl yapılır: Hata İşleme
Bu konuda hata işleme kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar verilmiştir. Bu örnekte, iletilerin hedef uç noktasına yönlendirilir. Bir ağ veya iletişimleri ilgili bir hata nedeniyle ileti teslim edilmemesi durumunda (<xref:System.ServiceModel.CommunicationException>), iletinin diğer uç noktasına gönderilir.  
  
> [!NOTE]
>  Bir ağ hatası benzetimini yapmak için bu örnekte kullanılan hedef uç nokta adresi yanlış içerir. Bu uç nokta başarısız herhangi bir hizmet olarak yönlendirilmiş iletiler belirtilen adresinde dinlemede.  
  
> [!NOTE]
>  Bu konuda yer alan örnek zaman aşımı ayarları açıkça tartışılmaz olsa da, bunlar dikkate hata işleme kullanırken almanız gerekir. Hatalarla karşılaşılırsa, istemci bir yanıt almadan önce karşılaştı ek bir gecikme olacaktır. Yönlendirme için yedek bir uç nokta iletiyi göndermeyi deneme hizmetini sırasında hata alındı olmasıdır. Zaman aşımı değerlerini ilişkili birincil ve yedek hedef uç noktaları büyük, ileti yedekleme listesinde birden fazla uç noktası üzerinden başarıyla gönderilmeden önce başarısız olarak istemci kadar uzun bir gecikme.  
>   
>  Yönlendirme Hizmeti Filtresi ile ilişkili tüm uç noktaları için zaman aşımı değeri toplamı eşit bir maksimum gecikme karşılaşabileceği olduğundan, istemcide beklenen zaman aşımı süresini buna göre artırmak öneririz.  
  
### <a name="implement-error-handling"></a>Uygulama hata işleme  
  
1.  Temel yönlendirme hizmeti yapılandırma hizmeti tarafından sunulan hizmet uç noktası belirterek oluşturun. Aşağıdaki örnek, iletileri almak için kullanılan bir tek hizmet uç noktası tanımlar. Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination. DeadDestination endpoint çalışan bir hizmeti başvurmuyor ve iletileri Bu uç noktaya gönderirken bir ağ hatası benzetimini yapmak için kullanılan bir adres içeriyor.  
  
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
  
2.  Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtrelerini tanımlayın.  Bu örnekte, bir MatchAll filtre yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  Bir ileti için bir ağ veya iletişim hatası durumunda birincil hedef uç noktasına gönderirken gönderilen uç noktaları içeren yedekleme uç nokta listesi tanımlayın. Aşağıdaki örnek, bir uç nokta içeren bir yedekleme listesini tanımlar; Ancak, birden çok uç nokta yedek listesinde belirtilebilir.  
  
     Yedek listeyi içeren birden fazla uç noktası, bir ağ veya yönlendirme hizmeti iletişim hatası oluştuğunda listedeki Birinci uç nokta ileti göndermeye çalışır. Bu uç noktaya gönderirken bir ağ veya iletişim hatası oluşursa, listede yer alan sonraki uç nokta ileti göndermek yönlendirme hizmeti çalışır. Hizmet, iletiyi başarıyla gönderdiği, bir ağ veya iletişimleri ile ilgili hata, tüm yedekleme uç noktaları dönmek veya ileti gönderilir ve uç nokta ağ olmayan döndürür kadar yedekleme uç noktası listesindeki her bir uç nokta için ileti gönderilirken devam eder, iletişim ilgili olmayan bir hata oluştu.  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  Filtre deadDestination uç noktası ve yedekleme uç nokta listesi ile ilişkilendirir Filtresi tablosu tanımlayın.  Yönlendirme hizmeti, ilk filtresiyle ilişkili hedef uç nokta ileti göndermeye çalışır. DeadDestination çalışan bir hizmete başvurmayan bir adresi içerdiğinden, bu bir ağ hatası oluşur. Yönlendirme hizmeti backupEndpointlist belirtilen uç nokta ileti göndermek daha sonra çalışır.  
  
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
  
5.  Filtre tablosunda bulunan filtre karşı gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile Filtresi tablosu ilişkilendirmelisiniz.  Aşağıdaki örnek, hizmet uç noktaları ile özellikle görüntüyle "filterTable1" gösterir.  
  
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
 Yapılandırma dosyası tam bir listesi aşağıda verilmiştir.  
  
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
