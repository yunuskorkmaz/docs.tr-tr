---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: fc1930889235805d68d88aa8080f8f9fb3235612
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933034"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="4665b-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4665b-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="4665b-102">Eş kanala özgü TCP mesajlaşma için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4665b-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="4665b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4665b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4665b-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4665b-104">\<bindings></span></span>  
<span data-ttu-id="4665b-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4665b-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4665b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4665b-106">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4665b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4665b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4665b-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="4665b-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4665b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4665b-109">Attributes</span></span>  
  
|<span data-ttu-id="4665b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4665b-110">Attribute</span></span>|<span data-ttu-id="4665b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4665b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4665b-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="4665b-112">closeTimeout</span></span>|<span data-ttu-id="4665b-113">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4665b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4665b-114">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4665b-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4665b-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4665b-116">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="4665b-116">listenIPAddress</span></span>|<span data-ttu-id="4665b-117">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4665b-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="4665b-118">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4665b-118">The default is `null`.</span></span>|  
|<span data-ttu-id="4665b-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4665b-119">maxBufferPoolSize</span></span>|<span data-ttu-id="4665b-120">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4665b-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4665b-121">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="4665b-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="4665b-122">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="4665b-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4665b-123">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4665b-124">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4665b-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4665b-125">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="4665b-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4665b-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4665b-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="4665b-127">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4665b-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4665b-128">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="4665b-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4665b-129">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4665b-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4665b-130">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4665b-130">The default is 65536.</span></span>|  
|<span data-ttu-id="4665b-131">name</span><span class="sxs-lookup"><span data-stu-id="4665b-131">name</span></span>|<span data-ttu-id="4665b-132">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4665b-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4665b-133">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4665b-134">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4665b-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4665b-135">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="4665b-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4665b-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4665b-136">openTimeout</span></span>|<span data-ttu-id="4665b-137">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4665b-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4665b-138">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4665b-139">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4665b-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4665b-140">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="4665b-140">port</span></span>|<span data-ttu-id="4665b-141">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4665b-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="4665b-142">Bu değer ve <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort>arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="4665b-143">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="4665b-143">The default is 0.</span></span>|  
|<span data-ttu-id="4665b-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4665b-144">receiveTimeout</span></span>|<span data-ttu-id="4665b-145">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4665b-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4665b-146">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4665b-147">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4665b-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="4665b-148">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="4665b-148">sendTimeout</span></span>|<span data-ttu-id="4665b-149">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4665b-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4665b-150">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4665b-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4665b-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4665b-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4665b-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4665b-152">Child Elements</span></span>  
  
|<span data-ttu-id="4665b-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="4665b-153">Element</span></span>|<span data-ttu-id="4665b-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4665b-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4665b-155">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4665b-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4665b-156">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4665b-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4665b-157">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4665b-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="4665b-158">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="4665b-158">\<resolver></span></span>](resolver.md)|<span data-ttu-id="4665b-159">Bu bağlama tarafından eş ağ içindeki düğümlerin uç nokta IP adreslerine bir eş ağ KIMLIĞINI çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="4665b-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="4665b-160">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4665b-160">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="4665b-161">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4665b-161">Defines the security settings for the message.</span></span> <span data-ttu-id="4665b-162">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4665b-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4665b-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4665b-163">Parent Elements</span></span>  
  
|<span data-ttu-id="4665b-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="4665b-164">Element</span></span>|<span data-ttu-id="4665b-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4665b-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4665b-166">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4665b-166">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4665b-167">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4665b-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4665b-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4665b-168">Remarks</span></span>  
 <span data-ttu-id="4665b-169">Bu bağlama, TCP üzerinden eş aktarım kullanarak eşler arası veya çok taraflı uygulamalar oluşturmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4665b-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="4665b-170">Her eş düğüm, bu bağlama türüyle tanımlanmış birden çok eş kanalını barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="4665b-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4665b-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="4665b-171">Example</span></span>  
 <span data-ttu-id="4665b-172">Aşağıdaki örnek, bir eş kanal kullanarak çok taraflı iletişim sağlayan NetPeerTcpBinding bağlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4665b-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="4665b-173">Bu bağlamayı kullanmanın ayrıntılı bir senaryosu için bkz. [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4665b-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="4665b-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4665b-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="4665b-175">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4665b-175">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4665b-176">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4665b-176">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4665b-177">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4665b-177">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4665b-178">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4665b-178">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="4665b-179">[NET eş TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4665b-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="4665b-180">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="4665b-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
