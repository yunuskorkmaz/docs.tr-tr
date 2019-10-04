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
# <a name="how-to-error-handling"></a><span data-ttu-id="6e108-102">Nasıl yapılır: Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="6e108-102">How To: Error Handling</span></span>

<span data-ttu-id="6e108-103">Bu konuda, hata işleme kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e108-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="6e108-104">Bu örnekte, iletiler bir hedef uç noktaya yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6e108-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="6e108-105">Bir ileti ağ veya iletişimle ilgili bir başarısızlık (<xref:System.ServiceModel.CommunicationException>) nedeniyle iletilemez, ileti alternatif bir uç noktaya yeniden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6e108-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="6e108-106">Bir ağ hatasının benzetimini yapmak için, bu örnekte kullanılan hedef uç noktası yanlış bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6e108-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="6e108-107">Belirtilen adreste hiçbir hizmet dinlemede olmadığından, bu uç noktaya yönlendirilen iletiler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6e108-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>

> [!NOTE]
> <span data-ttu-id="6e108-108">Bu konuda yer alan örnek, zaman aşımı ayarlarını açıkça ele almadığı sürece, hata işleme kullanırken bunları dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e108-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="6e108-109">Hatalarla karşılaşıldığında, istemci yanıt almadan önce ek bir gecikme ile karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="6e108-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="6e108-110">Bunun nedeni, hatanın yönlendirme hizmetinde alınması ve daha sonra iletiyi bir yedekleme uç noktasına göndermenizi dener.</span><span class="sxs-lookup"><span data-stu-id="6e108-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="6e108-111">Birincil ve yedek hedef uç noktalarıyla ilişkili zaman aşımı değerleri büyükse, ileti başarıyla gönderilmeden önce yedekleme listesindeki birden fazla uç nokta üzerinde hata verdiğinde, istemci uzun bir gecikmeyle karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="6e108-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>
>
> <span data-ttu-id="6e108-112">Yönlendirme hizmeti bir filtreyle ilişkili tüm uç noktalar için zaman aşımı değerinin toplamına eşit olan en büyük gecikmeyle karşılaştırabileceğinizden, istemcide beklenen zaman aşımını de artırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="6e108-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>

### <a name="implement-error-handling"></a><span data-ttu-id="6e108-113">Hata Işlemeyi Uygula</span><span class="sxs-lookup"><span data-stu-id="6e108-113">Implement Error Handling</span></span>

1. <span data-ttu-id="6e108-114">Hizmet tarafından açığa çıkarılan hizmet uç noktasını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6e108-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="6e108-115">Aşağıdaki örnek, ileti almak için kullanılan tek bir hizmet uç noktasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e108-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="6e108-116">Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination.</span><span class="sxs-lookup"><span data-stu-id="6e108-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="6e108-117">DeadDestination uç noktası, çalışan bir hizmete başvurmayan ve bu uç noktaya ileti gönderilirken bir ağ başarısızlığının benzetimini yapmak için kullanılan bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6e108-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>

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

2. <span data-ttu-id="6e108-118">İletileri hedef uç noktalara yönlendirmek için kullanılan filtreleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6e108-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="6e108-119">Bu örnekte, bir MatchAll filtresi, yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e108-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>

    ```xml
    <filters>
      <!-- Create a MatchAll filter which will catch all messages -->
      <filter name="MatchAllFilter1" filterType="MatchAll" />
    </filters>
    ```

3. <span data-ttu-id="6e108-120">Bir iletinin bir ağ olayında gönderildiği bitiş noktalarını veya birincil hedef uç noktasına gönderilirken iletişim hatasını içeren yedekleme uç noktası listesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6e108-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="6e108-121">Aşağıdaki örnek bir uç nokta içeren bir yedekleme listesi tanımlar; Ancak, bir yedekleme listesinde birden fazla uç nokta belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6e108-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>

     <span data-ttu-id="6e108-122">Yedekleme listesi birden çok uç nokta içeriyorsa, bir ağ veya iletişim hatası oluştuğunda, ileti listedeki ilk uç noktaya gönderilmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="6e108-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="6e108-123">Bu uç noktaya gönderilirken bir ağ veya iletişim hatası oluşursa, yönlendirme hizmeti iletiyi listede yer alan bir sonraki uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="6e108-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="6e108-124">Hizmet, ileti başarıyla gönderilene kadar yedekleme uç noktası listesindeki her bir uç noktaya iletiyi göndermeye devam eder, tüm yedekleme uç noktaları ağ veya iletişimlerle ilgili bir hata döndürmüyor, ya da ileti gönderilir ve uç nokta ağ olmayan bir değer döndürür. iletişimlerle ilgili olmayan hata.</span><span class="sxs-lookup"><span data-stu-id="6e108-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>

    ```xml
    <backupLists>
      <backupList name="backupEndpointList">
          <add endpointName="realDestination" />
      </backupList>
    </backupLists>
    ```

4. <span data-ttu-id="6e108-125">Filtreyi deadDestination bitiş noktasıyla ve yedekleme uç noktası listesiyle ilişkilendiren filtre tablosunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6e108-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="6e108-126">Yönlendirme hizmeti ilk olarak iletiyi filtreyle ilişkili hedef uç noktaya gönderilmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="6e108-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="6e108-127">DeadDestination, çalışan bir hizmete başvurmayan bir adres içerdiğinden, bu durum Ağ hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6e108-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="6e108-128">Yönlendirme hizmeti daha sonra iletiyi backupEndpointList öğesinde belirtilen uç noktaya gönderme girişiminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6e108-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointList.</span></span>

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

5. <span data-ttu-id="6e108-129">Gelen iletileri filtre tablosunda bulunan filtreye karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e108-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="6e108-130">Aşağıdaki örnek, "filterTable1" ın hizmet uç noktalarıyla ilişkilendirilmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e108-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>

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

## <a name="example"></a><span data-ttu-id="6e108-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e108-131">Example</span></span>

<span data-ttu-id="6e108-132">Yapılandırma dosyasının tüm listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6e108-132">The following is a complete listing of the configuration file:</span></span>

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
