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
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="e2b16-102">Nasıl yapılır: Hizmet Verilerini Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="e2b16-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="e2b16-103">Bu konu, birden çok örneğini aynı hedef hizmeti arasında bölüm iletileri için gereken temel adımlarda özetler.</span><span class="sxs-lookup"><span data-stu-id="e2b16-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="e2b16-104">Hizmet verilerini bölümlendirme, genellikle daha iyi hizmet kalitesi sağlamak amacıyla bir hizmeti ölçeklendirmek gerektiğinde veya farklı müşterilerden gelen istekleri belirli bir şekilde işlemek üzere gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2b16-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="e2b16-105">Örneğin, yüksek bir değer veya "Altın" müşterilerden iletileri standart müşteri iletilerden daha yüksek bir öncelik işlenecek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e2b16-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="e2b16-106">Bu örnekte, iletilerin regularCalc hizmetin iki örneğini birine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e2b16-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="e2b16-107">Her iki hizmet örneklerini aynıdır; ancak calculator1 uç nokta işlemleri iletiler tarafından temsil edilen hizmet yüksek değerli müşterilerden hesaplayıcı 2 bitiş noktası diğer müşterilerden gelen iletileri işleme alınan</span><span class="sxs-lookup"><span data-stu-id="e2b16-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="e2b16-108">İstemciden gönderilen ileti için ileti yönlendirileceğini hangi hizmet örneğine tanımlamak için kullanılan herhangi bir benzersiz veri yok.</span><span class="sxs-lookup"><span data-stu-id="e2b16-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="e2b16-109">Belirli bir hedef hizmet için rota verilerini her bir istemciye izin vermek için iletileri almak için kullanılan iki hizmet uç noktaları gerçekleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e2b16-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2b16-110">Bu örnek bölüm verilere özel uç noktaları kullanırken, bu da üstbilgi veya gövde verileri gibi ileti kendi içinde yer alan bilgileri kullanarak bunu sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2b16-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="e2b16-111">Uygulama hizmet verilerini bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="e2b16-111">Implement Service Data Partitioning</span></span>  
  
1.  <span data-ttu-id="e2b16-112">Temel yönlendirme hizmeti yapılandırma hizmeti tarafından sunulan hizmet uç noktalarına belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2b16-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="e2b16-113">Aşağıdaki örnek, iletileri almak için kullanılan iki uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2b16-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="e2b16-114">Ayrıca, regularCalc hizmet örneklerine ileti göndermek için kullanılan istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2b16-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2.  <span data-ttu-id="e2b16-115">Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtrelerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e2b16-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="e2b16-116">Bu örnekte, EndpointName filtresi, hangi hizmet uç noktası iletisi aldı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2b16-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="e2b16-117">Aşağıdaki örnek, filtreleri ve gerekli yönlendirme bölüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2b16-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3.  <span data-ttu-id="e2b16-118">Her filtre bir istemci uç noktası ile ilişkilendirir Filtresi tablosu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e2b16-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="e2b16-119">Bu örnekte, ileti üzerinden alındı belirli bir uç göre yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e2b16-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="e2b16-120">İletinin yalnızca iki olası filtrelerden birini eşleştirebilirsiniz olduğundan, hangi filtreleri değerlendirilir siparişe denetlemek için filtre öncelik kullanma gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e2b16-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="e2b16-121">Aşağıdaki filtre tablosunda tanımlar ve daha önce tanımlanan filtreler ekler.</span><span class="sxs-lookup"><span data-stu-id="e2b16-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4.  <span data-ttu-id="e2b16-122">Tabloda bulunan filtreleriyle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile Filtresi tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e2b16-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="e2b16-123">Aşağıdaki örnek, hizmet uç noktaları ile özellikle görüntüyle "filterTable1" gösterir:</span><span class="sxs-lookup"><span data-stu-id="e2b16-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e2b16-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2b16-124">Example</span></span>  
 <span data-ttu-id="e2b16-125">Yapılandırma dosyası tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2b16-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2b16-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2b16-126">See Also</span></span>  
 [<span data-ttu-id="e2b16-127">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e2b16-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
