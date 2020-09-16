---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 5fe221c5ec6c51afb199b2c66eab9d72cdfd750b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556147"
---
# \<netPeerTcpBinding>
<span data-ttu-id="485d9-101">Eş kanala özgü TCP mesajlaşma için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="485d9-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="485d9-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="485d9-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="485d9-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="485d9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="485d9-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="485d9-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="485d9-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="485d9-105">Attributes</span></span>  
  
|<span data-ttu-id="485d9-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="485d9-106">Attribute</span></span>|<span data-ttu-id="485d9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485d9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="485d9-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="485d9-108">closeTimeout</span></span>|<span data-ttu-id="485d9-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="485d9-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="485d9-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="485d9-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="485d9-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="485d9-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="485d9-112">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="485d9-112">listenIPAddress</span></span>|<span data-ttu-id="485d9-113">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="485d9-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="485d9-114">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="485d9-114">The default is `null`.</span></span>|  
|<span data-ttu-id="485d9-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="485d9-115">maxBufferPoolSize</span></span>|<span data-ttu-id="485d9-116">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="485d9-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="485d9-117">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="485d9-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="485d9-118">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="485d9-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="485d9-119">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="485d9-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="485d9-120">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="485d9-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="485d9-121">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="485d9-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="485d9-122">Değerini</span><span class="sxs-lookup"><span data-stu-id="485d9-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="485d9-123">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="485d9-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="485d9-124">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="485d9-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="485d9-125">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="485d9-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="485d9-126">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="485d9-126">The default is 65536.</span></span>|  
|<span data-ttu-id="485d9-127">name</span><span class="sxs-lookup"><span data-stu-id="485d9-127">name</span></span>|<span data-ttu-id="485d9-128">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="485d9-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="485d9-129">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="485d9-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="485d9-130">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="485d9-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="485d9-131">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="485d9-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="485d9-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="485d9-132">openTimeout</span></span>|<span data-ttu-id="485d9-133">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="485d9-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="485d9-134">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="485d9-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="485d9-135">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="485d9-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="485d9-136">port</span><span class="sxs-lookup"><span data-stu-id="485d9-136">port</span></span>|<span data-ttu-id="485d9-137">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="485d9-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="485d9-138">Bu değer ve arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="485d9-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="485d9-139">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="485d9-139">The default is 0.</span></span>|  
|<span data-ttu-id="485d9-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="485d9-140">receiveTimeout</span></span>|<span data-ttu-id="485d9-141"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="485d9-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="485d9-142">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="485d9-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="485d9-143">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="485d9-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="485d9-144">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="485d9-144">sendTimeout</span></span>|<span data-ttu-id="485d9-145"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="485d9-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="485d9-146">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="485d9-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="485d9-147">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="485d9-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="485d9-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="485d9-148">Child Elements</span></span>  
  
|<span data-ttu-id="485d9-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="485d9-149">Element</span></span>|<span data-ttu-id="485d9-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485d9-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="485d9-151">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="485d9-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="485d9-152">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="485d9-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="485d9-153">Bu bağlama tarafından eş ağ içindeki düğümlerin uç nokta IP adreslerine bir eş ağ KIMLIĞINI çözümlemek için kullanılan bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="485d9-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="485d9-154">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="485d9-154">Defines the security settings for the message.</span></span> <span data-ttu-id="485d9-155">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="485d9-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="485d9-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="485d9-156">Parent Elements</span></span>  
  
|<span data-ttu-id="485d9-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="485d9-157">Element</span></span>|<span data-ttu-id="485d9-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485d9-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="485d9-159">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="485d9-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="485d9-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="485d9-160">Remarks</span></span>  
 <span data-ttu-id="485d9-161">Bu bağlama, TCP üzerinden eş aktarım kullanarak eşler arası veya çok taraflı uygulamalar oluşturmaya yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="485d9-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="485d9-162">Her eş düğüm, bu bağlama türüyle tanımlanmış birden çok eş kanalını barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="485d9-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="485d9-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="485d9-163">Example</span></span>  
 <span data-ttu-id="485d9-164">Aşağıdaki örnek, bir eş kanal kullanarak çok taraflı iletişim sağlayan NetPeerTcpBinding bağlamasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="485d9-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="485d9-165">Bu bağlamayı kullanmanın ayrıntılı bir senaryosu için bkz. [net peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="485d9-165">For a detailed scenario of using this binding, see [Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="485d9-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="485d9-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="485d9-167">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="485d9-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="485d9-168">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="485d9-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="485d9-169">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="485d9-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="485d9-170">[NET eş TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="485d9-170">[Net Peer TCP](/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="485d9-171">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="485d9-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
