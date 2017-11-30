---
title: "Nasıl yapılır: Hata İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de566e39-9358-44ff-8244-780f6b799966
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5bcab65eb98684820a84968f15ba80de3c5b60de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-error-handling"></a><span data-ttu-id="478ef-102">Nasıl yapılır: Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="478ef-102">How To: Error Handling</span></span>
<span data-ttu-id="478ef-103">Bu konuda hata işleme kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="478ef-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="478ef-104">Bu örnekte, iletilerin hedef uç noktasına yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="478ef-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="478ef-105">Bir ağ veya iletişimleri ilgili bir hata nedeniyle ileti teslim edilmemesi durumunda (<xref:System.ServiceModel.CommunicationException>), iletinin diğer uç noktasına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="478ef-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="478ef-106">Bir ağ hatası benzetimini yapmak için bu örnekte kullanılan hedef uç nokta adresi yanlış içerir.</span><span class="sxs-lookup"><span data-stu-id="478ef-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="478ef-107">Bu uç nokta başarısız herhangi bir hizmet olarak yönlendirilmiş iletiler belirtilen adresinde dinlemede.</span><span class="sxs-lookup"><span data-stu-id="478ef-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="478ef-108">Bu konuda yer alan örnek zaman aşımı ayarları açıkça tartışılmaz olsa da, bunlar dikkate hata işleme kullanırken almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="478ef-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="478ef-109">Hatalarla karşılaşılırsa, istemci bir yanıt almadan önce karşılaştı ek bir gecikme olacaktır.</span><span class="sxs-lookup"><span data-stu-id="478ef-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="478ef-110">Yönlendirme için yedek bir uç nokta iletiyi göndermeyi deneme hizmetini sırasında hata alındı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="478ef-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="478ef-111">Zaman aşımı değerlerini ilişkili birincil ve yedek hedef uç noktaları büyük, ileti yedekleme listesinde birden fazla uç noktası üzerinden başarıyla gönderilmeden önce başarısız olarak istemci kadar uzun bir gecikme.</span><span class="sxs-lookup"><span data-stu-id="478ef-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="478ef-112">Yönlendirme Hizmeti Filtresi ile ilişkili tüm uç noktaları için zaman aşımı değeri toplamı eşit bir maksimum gecikme karşılaşabileceği olduğundan, istemcide beklenen zaman aşımı süresini buna göre artırmak öneririz.</span><span class="sxs-lookup"><span data-stu-id="478ef-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="478ef-113">Uygulama hata işleme</span><span class="sxs-lookup"><span data-stu-id="478ef-113">Implement Error Handling</span></span>  
  
1.  <span data-ttu-id="478ef-114">Temel yönlendirme hizmeti yapılandırma hizmeti tarafından sunulan hizmet uç noktası belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="478ef-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="478ef-115">Aşağıdaki örnek, iletileri almak için kullanılan bir tek hizmet uç noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="478ef-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="478ef-116">Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination.</span><span class="sxs-lookup"><span data-stu-id="478ef-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="478ef-117">DeadDestination endpoint çalışan bir hizmeti başvurmuyor ve iletileri Bu uç noktaya gönderirken bir ağ hatası benzetimini yapmak için kullanılan bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="478ef-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2.  <span data-ttu-id="478ef-118">Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtrelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="478ef-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="478ef-119">Bu örnekte, bir MatchAll filtre yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="478ef-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3.  <span data-ttu-id="478ef-120">Bir ileti için bir ağ veya iletişim hatası durumunda birincil hedef uç noktasına gönderirken gönderilen uç noktaları içeren yedekleme uç nokta listesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="478ef-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="478ef-121">Aşağıdaki örnek, bir uç nokta içeren bir yedekleme listesini tanımlar; Ancak, birden çok uç nokta yedek listesinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="478ef-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="478ef-122">Yedek listeyi içeren birden fazla uç noktası, bir ağ veya yönlendirme hizmeti iletişim hatası oluştuğunda listedeki Birinci uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="478ef-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="478ef-123">Bu uç noktaya gönderirken bir ağ veya iletişim hatası oluşursa, listede yer alan sonraki uç nokta ileti göndermek yönlendirme hizmeti çalışır.</span><span class="sxs-lookup"><span data-stu-id="478ef-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="478ef-124">Hizmet, iletiyi başarıyla gönderdiği, bir ağ veya iletişimleri ile ilgili hata, tüm yedekleme uç noktaları dönmek veya ileti gönderilir ve uç nokta ağ olmayan döndürür kadar yedekleme uç noktası listesindeki her bir uç nokta için ileti gönderilirken devam eder, iletişim ilgili olmayan bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="478ef-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4.  <span data-ttu-id="478ef-125">Filtre deadDestination uç noktası ve yedekleme uç nokta listesi ile ilişkilendirir Filtresi tablosu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="478ef-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="478ef-126">Yönlendirme hizmeti, ilk filtresiyle ilişkili hedef uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="478ef-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="478ef-127">DeadDestination çalışan bir hizmete başvurmayan bir adresi içerdiğinden, bu bir ağ hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="478ef-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="478ef-128">Yönlendirme hizmeti backupEndpointlist belirtilen uç nokta ileti göndermek daha sonra çalışır.</span><span class="sxs-lookup"><span data-stu-id="478ef-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5.  <span data-ttu-id="478ef-129">Filtre tablosunda bulunan filtre karşı gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile Filtresi tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="478ef-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="478ef-130">Aşağıdaki örnek, hizmet uç noktaları ile özellikle görüntüyle "filterTable1" gösterir.</span><span class="sxs-lookup"><span data-stu-id="478ef-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="478ef-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="478ef-131">Example</span></span>  
 <span data-ttu-id="478ef-132">Yapılandırma dosyası tam bir listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="478ef-132">Following is a complete listing of the configuration file.</span></span>  
  
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
