---
title: 'Nasıl yapılır: Hizmet Verilerini Bölümlendirme'
ms.date: 03/30/2017
ms.assetid: 1ccff72e-d76b-4e36-93a2-e51f7b32dc83
ms.openlocfilehash: 17cb80bf253491eb563d6fd45b5997e452f542e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047535"
---
# <a name="how-to-service-data-partitioning"></a><span data-ttu-id="d77b4-102">Nasıl yapılır: Hizmet Verilerini Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="d77b4-102">How To: Service Data Partitioning</span></span>
<span data-ttu-id="d77b4-103">Bu konuda, birden çok hedef hizmetin aynı örneğine bölüm iletileri için gerekli temel adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d77b4-103">This topic outlines the basic steps required to partition messages across multiple instances of the same destination service.</span></span> <span data-ttu-id="d77b4-104">Hizmet verilerini bölümlendirme, genellikle daha iyi hizmet kalitesini sağlamak için bir hizmeti ölçeklendirmek gerektiğinde veya farklı müşterilerden gelen istekleri belirli bir şekilde işlemek üzere gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d77b4-104">Service data partitioning is typically used when you need to scale a service in order to provide better quality of service, or when you need to handle requests from different customers in a specific way.</span></span> <span data-ttu-id="d77b4-105">Örneğin, yüksek bir değer veya "Altın" müşteriler gelen iletileri, standart bir müşteri iletilerden daha yüksek bir önceliğe işlenecek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d77b4-105">For example, messages from high value or "Gold" customers may need to be processed at a higher priority than messages from a standard customer.</span></span>  
  
 <span data-ttu-id="d77b4-106">Bu örnekte, iletilerin regularCalc hizmetin iki örneği birine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d77b4-106">In this example, messages are routed to one of two instances of the regularCalc service.</span></span> <span data-ttu-id="d77b4-107">Her iki hizmetin örneklerini aynıdır; ancak yüksek değerli müşterilerden hesaplayıcı 2 uç nokta calculator1 uç nokta işlemleri iletiler tarafından temsil edilen hizmet diğer müşterilerden gelen iletileri işleme alınan</span><span class="sxs-lookup"><span data-stu-id="d77b4-107">Both instances of the service are identical; however the service represented by the calculator1 endpoint processes messages received from high value customers, the calculator 2 endpoint processes messages from other customers</span></span>  
  
 <span data-ttu-id="d77b4-108">İstemciden gönderilen ileti için ileti yönlendirileceğini hangi hizmet örneğini tanımlamak için kullanılan herhangi bir benzersiz veri yok.</span><span class="sxs-lookup"><span data-stu-id="d77b4-108">The message sent from the client does not have any unique data that can be used to identify which service instance the message should be routed to.</span></span> <span data-ttu-id="d77b4-109">Her bir istemciye belirli hedef hizmet için rota verilerini izin vermek için ileti almak için kullanılacak olan iki hizmet uç noktaları uygular.</span><span class="sxs-lookup"><span data-stu-id="d77b4-109">To allow each client to route data to a specific destination service we will implement two service endpoints that will be used to receive messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d77b4-110">Bu örnek verileri bölümlemek için özel uç noktaları kullanırken, bu da üst bilgi veya gövdesinde veri gibi ileti kendisi içinde yer alan bilgileri kullanarak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d77b4-110">While this example uses specific endpoints to partition data, this could also be accomplished using information contained within the message itself such as header or body data.</span></span>  
  
### <a name="implement-service-data-partitioning"></a><span data-ttu-id="d77b4-111">Uygulama hizmeti veri bölümleme</span><span class="sxs-lookup"><span data-stu-id="d77b4-111">Implement Service Data Partitioning</span></span>  
  
1. <span data-ttu-id="d77b4-112">Temel yönlendirme hizmeti yapılandırmasını hizmet tarafından sunulan hizmet uç noktaları belirterek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d77b4-112">Create the basic Routing Service configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="d77b4-113">Aşağıdaki örnek, iletileri almak için kullanılan iki uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d77b4-113">The following example defines two endpoints, which will be used to receive messages.</span></span> <span data-ttu-id="d77b4-114">Ayrıca, regularCalc hizmet örnekleri için ileti göndermek için kullanılan istemci uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d77b4-114">It also defines the client endpoints, which are used to send messages to the regularCalc service instances.</span></span>  
  
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
  
2. <span data-ttu-id="d77b4-115">Hedef Uç noktalara iletileri yönlendirmek için kullanılan filtreler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d77b4-115">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="d77b4-116">Bu örnekte, Uçnoktaadı filtre, hangi hizmet uç noktası iletisi aldı belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d77b4-116">For this example, the EndpointName filter is used to determine which service endpoint received the message.</span></span> <span data-ttu-id="d77b4-117">Aşağıdaki örnek, gerekli yönlendirme bölüm ve filtreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d77b4-117">The following example defines the necessary routing section and filters.</span></span>  
  
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
  
3. <span data-ttu-id="d77b4-118">Her filtre bir istemci uç noktası ile ilişkilendirir filtre tablo tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d77b4-118">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="d77b4-119">Bu örnekte, ileti üzerinde alındı belirli bir uç göre yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d77b4-119">In this example, the message will be routed based on the specific endpoint it was received over.</span></span> <span data-ttu-id="d77b4-120">İletinin yalnızca iki olası filtrelerden birini eşleşebilir olduğundan, hangi filtrelerde değerlendirilir sırasını denetlemek için filtre önceliği kullanma gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="d77b4-120">Since the message can only match one of the two possible filters, there is no need for using filter priority to control to the order in which filters are evaluated.</span></span>  
  
     <span data-ttu-id="d77b4-121">Aşağıdaki filtre tabloyu tanımlayan ve daha önce tanımlanan filtreler ekler.</span><span class="sxs-lookup"><span data-stu-id="d77b4-121">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
       <filterTable name="filterTable1">  
         <!--add the filters to the message filter table-->  
         <add filterName="HighPriority" endpointName="CalcEndpoint1"/>  
         <add filterName="NormalPriority" endpointName="CalcEndpoint2"/>  
       </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="d77b4-122">Tabloda bulunan filtrelerle gelen iletileri değerlendirmek için yönlendirme davranışı kullanarak hizmet uç noktaları ile filtreleme tablosu ilişkilendirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d77b4-122">To evaluate incoming messages against the filters contained in the table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d77b4-123">Aşağıdaki örnek, hizmet uç noktaları ile ilişkilendirmeyi "filterTable1" gösterir:</span><span class="sxs-lookup"><span data-stu-id="d77b4-123">The following example demonstrates associating "filterTable1" with the service endpoints:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d77b4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d77b4-124">Example</span></span>  
 <span data-ttu-id="d77b4-125">Yapılandırma dosyasının tam bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d77b4-125">The following is a complete listing of the configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d77b4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d77b4-126">See also</span></span>

- [<span data-ttu-id="d77b4-127">Yönlendirme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d77b4-127">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
