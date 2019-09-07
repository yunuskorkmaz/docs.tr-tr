---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 48d7e10eddbf3ed2e2bfe3d04566d37ead5a1e04
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400154"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="08d15-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="08d15-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="08d15-102">Eş kanala özgü TCP mesajlaşma için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08d15-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
<span data-ttu-id="08d15-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08d15-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08d15-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="08d15-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="08d15-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="08d15-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="08d15-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netPeerTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="08d15-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d15-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08d15-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08d15-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08d15-108">Attributes and Elements</span></span>  
 <span data-ttu-id="08d15-109">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="08d15-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08d15-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08d15-110">Attributes</span></span>  
  
|<span data-ttu-id="08d15-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08d15-111">Attribute</span></span>|<span data-ttu-id="08d15-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d15-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08d15-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="08d15-113">closeTimeout</span></span>|<span data-ttu-id="08d15-114">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="08d15-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="08d15-115">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08d15-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="08d15-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="08d15-117">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="08d15-117">listenIPAddress</span></span>|<span data-ttu-id="08d15-118">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="08d15-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="08d15-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="08d15-119">The default is `null`.</span></span>|  
|<span data-ttu-id="08d15-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="08d15-120">maxBufferPoolSize</span></span>|<span data-ttu-id="08d15-121">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="08d15-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="08d15-122">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="08d15-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="08d15-123">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="08d15-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="08d15-124">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="08d15-125">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08d15-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="08d15-126">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="08d15-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="08d15-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="08d15-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="08d15-128">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="08d15-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="08d15-129">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="08d15-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="08d15-130">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08d15-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="08d15-131">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="08d15-131">The default is 65536.</span></span>|  
|<span data-ttu-id="08d15-132">name</span><span class="sxs-lookup"><span data-stu-id="08d15-132">name</span></span>|<span data-ttu-id="08d15-133">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="08d15-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="08d15-134">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="08d15-135">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="08d15-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="08d15-136">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="08d15-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="08d15-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="08d15-137">openTimeout</span></span>|<span data-ttu-id="08d15-138">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="08d15-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="08d15-139">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08d15-140">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="08d15-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="08d15-141">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="08d15-141">port</span></span>|<span data-ttu-id="08d15-142">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="08d15-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="08d15-143">Bu değer ve <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort>arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="08d15-144">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="08d15-144">The default is 0.</span></span>|  
|<span data-ttu-id="08d15-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="08d15-145">receiveTimeout</span></span>|<span data-ttu-id="08d15-146">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="08d15-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="08d15-147">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08d15-148">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="08d15-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="08d15-149">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="08d15-149">sendTimeout</span></span>|<span data-ttu-id="08d15-150">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="08d15-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="08d15-151">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08d15-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="08d15-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="08d15-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08d15-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08d15-153">Child Elements</span></span>  
  
|<span data-ttu-id="08d15-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="08d15-154">Element</span></span>|<span data-ttu-id="08d15-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d15-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08d15-156">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="08d15-156">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="08d15-157">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08d15-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="08d15-158">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="08d15-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="08d15-159">\<çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="08d15-159">\<resolver></span></span>](resolver.md)|<span data-ttu-id="08d15-160">Bu bağlama tarafından eş ağ içindeki düğümlerin uç nokta IP adreslerine bir eş ağ KIMLIĞINI çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="08d15-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="08d15-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="08d15-161">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="08d15-162">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08d15-162">Defines the security settings for the message.</span></span> <span data-ttu-id="08d15-163">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="08d15-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08d15-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08d15-164">Parent Elements</span></span>  
  
|<span data-ttu-id="08d15-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="08d15-165">Element</span></span>|<span data-ttu-id="08d15-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d15-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08d15-167">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="08d15-167">\<bindings></span></span>](bindings.md)|<span data-ttu-id="08d15-168">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="08d15-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d15-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08d15-169">Remarks</span></span>  
 <span data-ttu-id="08d15-170">Bu bağlama, TCP üzerinden eş aktarım kullanarak eşler arası veya çok taraflı uygulamalar oluşturmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="08d15-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="08d15-171">Her eş düğüm, bu bağlama türüyle tanımlanmış birden çok eş kanalını barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="08d15-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08d15-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="08d15-172">Example</span></span>  
 <span data-ttu-id="08d15-173">Aşağıdaki örnek, bir eş kanal kullanarak çok taraflı iletişim sağlayan NetPeerTcpBinding bağlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08d15-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="08d15-174">Bu bağlamayı kullanmanın ayrıntılı bir senaryosu için bkz. [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="08d15-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08d15-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08d15-175">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="08d15-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="08d15-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08d15-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="08d15-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08d15-178">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="08d15-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="08d15-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="08d15-179">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="08d15-180">[NET eş TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="08d15-180">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="08d15-181">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="08d15-181">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
