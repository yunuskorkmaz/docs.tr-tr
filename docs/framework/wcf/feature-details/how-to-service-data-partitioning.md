---
title: 'Nasıl yapılır: Hizmet Verilerini Bölümlendirme'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 49aefd88d73732a139a79f8c53d5beca44d4d4ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947866"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="4a2c7-102">Nasıl yapılır: Hizmet Verilerini Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="4a2c7-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="4a2c7-103">Bu konu başlığı altında, aynı hedef hizmetin birden çok örneğinde iletileri bölümlemek için gereken temel adımlar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="4a2c7-104">Hizmet verileri bölümlendirme genellikle, daha iyi hizmet kalitesi sağlamak için veya belirli bir şekilde farklı müşterilerden gelen istekleri işleyebilmeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="4a2c7-105">Örneğin, yüksek değerden veya "altın" müşterilerden gelen iletilerin, standart müşteriden gelen iletilerden daha yüksek bir önceliğe göre işlenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="4a2c7-106">Bu örnekte, iletiler regularCalc hizmetinin iki örneklerinden birine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="4a2c7-107">Hizmetin her iki örneği de aynıdır; Ancak, Calculator1 uç noktası tarafından temsil edilen hizmet, yüksek değerli müşterilerden alınan iletileri işlediğinde, hesaplayıcı 2 uç noktası diğer müşterilerden gelen iletileri işler</span><span class="sxs-lookup"><span data-stu-id="4a2c7-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="4a2c7-108">İstemciden gönderilen iletinin, iletinin hangi hizmet örneğine yönlendirildiğini belirlemek için kullanılabilecek benzersiz verileri yok.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="4a2c7-109">Her bir istemcinin verileri belirli bir hedef hizmete yönlendirmesine izin vermek için, ileti almak için kullanılacak iki hizmet uç noktası uygulayacağız.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a2c7-110">Bu örnek, verileri bölümlemek için belirli uç noktaları kullandığında, bu da ileti içinde başlık veya gövde verileri gibi bilgiler kullanılarak da gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="4a2c7-111">Hizmet veri bölümlendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="4a2c7-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="4a2c7-112">Hizmet tarafından sunulan hizmet uç noktalarını belirterek temel yönlendirme hizmeti yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="4a2c7-113">Aşağıdaki örnek, ileti almak için kullanılacak iki uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="4a2c7-114">Ayrıca, regularCalc hizmeti örneklerine ileti göndermek için kullanılan istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="4a2c7-115">İletileri hedef uç noktalara yönlendirmek için kullanılan filtreleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="4a2c7-116">Bu örnek için, EndpointName filtresi, iletiyi hangi hizmet uç noktasının aldığını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="4a2c7-117">Aşağıdaki örnek, gerekli Yönlendirme bölümünü ve filtreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="4a2c7-118">Her bir filtreyi bir istemci uç noktasıyla ilişkilendiren filtre tablosunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="4a2c7-119">Bu örnekte ileti, aldığı belirli uç noktaya göre yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="4a2c7-120">İleti yalnızca iki olası filtreden birini eşleştirebilir, ancak filtrelerin değerlendirileceği sırayı denetlemek için filtre önceliği kullanılmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="4a2c7-121">Aşağıda, filtre tablosu tanımlanmaktadır ve daha önce tanımlanan filtreler eklenir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="4a2c7-122">Gelen iletileri tabloda yer alan filtrelere karşı değerlendirmek için, yönlendirme davranışını kullanarak filtre tablosunu hizmet uç noktalarıyla ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="4a2c7-123">Aşağıdaki örnek, "filterTable1" ın hizmet uç noktaları ile ilişkilendirilmesini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4a2c7-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4a2c7-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a2c7-124">Example</span></span>  
 <span data-ttu-id="4a2c7-125">Yapılandırma dosyasının tüm listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a2c7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-126">See also</span></span>

- [<span data-ttu-id="4a2c7-127">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4a2c7-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
