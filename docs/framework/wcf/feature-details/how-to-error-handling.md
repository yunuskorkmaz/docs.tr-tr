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
# <a name="how-to-error-handling"></a><span data-ttu-id="b88c0-102">Nasıl yapılır: Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="b88c0-102">How To: Error Handling</span></span>
<span data-ttu-id="b88c0-103">Bu konuda, hata işleme kullanan bir yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-103">This topic outlines the basic steps required to create a routing configuration that uses error handling.</span></span> <span data-ttu-id="b88c0-104">Bu örnekte, bir hedef uç noktasına iletileri yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-104">In this example, messages are routed to a destination endpoint.</span></span> <span data-ttu-id="b88c0-105">Bir ağ veya iletişim ilgili bir hata nedeniyle bir ileti gönderilemezse (<xref:System.ServiceModel.CommunicationException>), ileti başka bir uç noktasına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-105">If a message cannot be delivered due to a network or communications-related failure (<xref:System.ServiceModel.CommunicationException>), the message is resent to an alternate endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b88c0-106">Bir ağ hatası benzetimini yapmak için bu örnekte kullanılan hedef uç nokta adresi yanlış içerir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-106">To simulate a network failure, the destination endpoint used in this example contains an incorrect address.</span></span> <span data-ttu-id="b88c0-107">Bu uç nokta başarısız kıl hiçbir hizmet olarak yönlendirilmiş iletiler belirtilen adresinde dinlemede.</span><span class="sxs-lookup"><span data-stu-id="b88c0-107">Messages routed to this endpoint fail as no service is listening on the specified address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b88c0-108">Bu konuda yer alan örnek zaman aşımı ayarlarını açıkça açıklanmamıştır, ancak bunlar dikkate hata işleme kullanırken atmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-108">While the example contained in this topic does not explicitly discuss time-out settings, you must take these into consideration when using error handling.</span></span> <span data-ttu-id="b88c0-109">Hatalarla karşılaştı, istemci yanıt almadan önce karşılaştı, ek bir gecikme olur.</span><span class="sxs-lookup"><span data-stu-id="b88c0-109">When errors are encountered, there will be an additional delay encountered before the client receives a response.</span></span> <span data-ttu-id="b88c0-110">Hata yönlendirme yapılacak bir yedekleme uç noktasına göndermesi dener hizmetinin, alınan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-110">This is because the error is received at the Routing Service, which then attempts to send the message to a backup endpoint.</span></span> <span data-ttu-id="b88c0-111">Zaman aşımı değerlerini ilişkili birincil ve yedek hedef uç noktaları büyük olduğundan, başarıyla gönderilmeden önce ileti yedekleme listesinde birden fazla uç nokta üzerinde başarısız olarak istemci kadar uzun bir gecikme.</span><span class="sxs-lookup"><span data-stu-id="b88c0-111">If the time-out values associated with the primary and backup destination endpoints are large, the client could experience a long delay as the message fails over multiple endpoints in the backup list before being successfully sent.</span></span>  
>   
>  <span data-ttu-id="b88c0-112">Yönlendirme hizmeti, bir filtre ile ilişkili tüm uç noktalar için zaman aşımı değerini toplamına eşit en büyük gecikme karşılaşabilirsiniz olduğundan, buna göre istemcide beklenen zaman aşımını artırın öneririz.</span><span class="sxs-lookup"><span data-stu-id="b88c0-112">Since the Routing Service could encounter a maximum delay equal to the sum of the time-out value for all endpoints associated with a filter, we recommend that you increase the expected time-out at the client accordingly.</span></span>  
  
### <a name="implement-error-handling"></a><span data-ttu-id="b88c0-113">Hata işleme uygulama</span><span class="sxs-lookup"><span data-stu-id="b88c0-113">Implement Error Handling</span></span>  
  
1. <span data-ttu-id="b88c0-114">Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktası belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b88c0-114">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="b88c0-115">Aşağıdaki örnek, iletileri almak için kullanılan bir tek hizmet uç noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b88c0-115">The following example defines a single service endpoint, which is used to receive messages.</span></span> <span data-ttu-id="b88c0-116">Ayrıca, ileti göndermek için kullanılan istemci uç noktalarını tanımlar; deadDestination ve realDestination.</span><span class="sxs-lookup"><span data-stu-id="b88c0-116">It also defines the client endpoints that are used to send messages; deadDestination and realDestination.</span></span> <span data-ttu-id="b88c0-117">DeadDestination uç nokta çalışan bir hizmete başvurmuyor ve bu uç noktaya iletileri gönderirken, bir ağ hatası benzetimini yapmak için kullanılan bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b88c0-117">The deadDestination endpoint contains an address that does not reference a running service and is used to simulate a network failure when sending messages to this endpoint.</span></span>  
  
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
  
2. <span data-ttu-id="b88c0-118">Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b88c0-118">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="b88c0-119">Bu örnekte, MatchAll filtre, yönlendirme hizmeti tarafından alınan tüm iletileri eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-119">For this example, a MatchAll filter is used to match all messages received by the Routing Service.</span></span>  
  
    ```xml  
    <filters>  
      <!-- Create a MatchAll filter which will catch all messages -->  
      <filter name="MatchAllFilter1" filterType="MatchAll" />  
    </filters>  
    ```  
  
3. <span data-ttu-id="b88c0-120">Bir ileti bir ağ veya iletişim hatası durumunda birincil hedef uç noktasına gönderilirken gönderilen uç noktaları içeren yedekleme uç nokta listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b88c0-120">Define the backup endpoint list, which contains the endpoints that a message is sent to in the event of a network or communications failure when sending to the primary destination endpoint.</span></span> <span data-ttu-id="b88c0-121">Aşağıdaki örnek, bir uç nokta içeren bir yedekleme listesini tanımlar; Ancak, birden fazla uç nokta yedekleme listesinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-121">The following example defines a backup list that contains one endpoint; however, multiple endpoints can be specified in a backup list.</span></span>  
  
     <span data-ttu-id="b88c0-122">Yedekleme listesinde birden fazla uç noktası, bir ağ içeriyorsa veya yönlendirme hizmeti iletişim hatası oluşur, listedeki ilk uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-122">If the backup list contains multiple endpoints, when a network or communications failure occurs the Routing Service attempts to send the message to the first endpoint in the list.</span></span> <span data-ttu-id="b88c0-123">Bu uç noktaya gönderirken bir ağ veya iletişim hatası meydana gelirse, yönlendirme hizmeti listede yer alan sonraki uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-123">If a network or communications failure occurs when sending to this endpoint, the Routing Service attempts to send the message to the next endpoint contained in the list.</span></span> <span data-ttu-id="b88c0-124">Hizmet, ileti başarıyla gönderildi, tüm yedekleme uç noktaları bir ağ veya iletişimleri ile ilgili bir hata döndürür veya ileti gönderilir ve ağ dışı uç noktanın döndürdüğü kadar yedekleme uç noktası listesindeki her bir uç nokta için ileti gönderilirken devam eder iletişim ilgili olmayan bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b88c0-124">The service continues sending the message to each endpoint in the backup endpoint list until the message is successfully sent, all backup endpoints return a network or communications-related error, or the message is sent and the endpoint returns a non-network, non-communications-related error.</span></span>  
  
    ```xml  
    <backupLists>          
      <backupList name="backupEndpointList">  
          <add endpointName="realDestination" />  
      </backupList>  
    </backupLists>  
    ```  
  
4. <span data-ttu-id="b88c0-125">Filtre deadDestination uç nokta ve yedekleme uç nokta listesi ile ilişkilendirir filtre tablo tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b88c0-125">Define the filter table, which associates the filter with the deadDestination endpoint and the backup endpoint list.</span></span>  <span data-ttu-id="b88c0-126">Yönlendirme hizmeti, ilk filtresiyle ilişkili hedef uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-126">The Routing Service first attempts to send the message to the destination endpoint associated with the filter.</span></span> <span data-ttu-id="b88c0-127">DeadDestination çalışan bir hizmete başvurmuyor bir adres içerdiğinden, bu bir ağ hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b88c0-127">Since the deadDestination contains an address that does not refer to a running service, this results in a network error.</span></span> <span data-ttu-id="b88c0-128">Yönlendirme hizmeti, ardından backupEndpointlist içinde belirtilen uç nokta ileti göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b88c0-128">The Routing Service then attempts to send the message to the endpoint specified in the backupEndpointlist.</span></span>  
  
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
  
5. <span data-ttu-id="b88c0-129">Filtre tablosunda yer alan filtre karşı gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b88c0-129">To evaluate incoming messages against the filter contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span>  <span data-ttu-id="b88c0-130">Aşağıdaki örnek, hizmet uç noktaları ile ilişkilendirmeyi "filterTable1" gösterir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-130">The following example demonstrates associating "filterTable1" with the service endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b88c0-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="b88c0-131">Example</span></span>  
 <span data-ttu-id="b88c0-132">Yapılandırma dosyasının tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b88c0-132">Following is a complete listing of the configuration file.</span></span>  
  
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
