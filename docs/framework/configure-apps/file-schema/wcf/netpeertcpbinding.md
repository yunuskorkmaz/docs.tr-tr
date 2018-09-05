---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 9032372f8e3344e9b1021be19a32230986b328a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513286"
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="05c8a-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="05c8a-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="05c8a-103">Eş kanallı belirli TCP Mesajlaşma için bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05c8a-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="05c8a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05c8a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="05c8a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="05c8a-105">\<bindings></span></span>  
<span data-ttu-id="05c8a-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="05c8a-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c8a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05c8a-107">Syntax</span></span>  
  
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
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05c8a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05c8a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05c8a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05c8a-110">Attributes</span></span>  
  
|<span data-ttu-id="05c8a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05c8a-111">Attribute</span></span>|<span data-ttu-id="05c8a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c8a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05c8a-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="05c8a-113">closeTimeout</span></span>|<span data-ttu-id="05c8a-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="05c8a-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="05c8a-115">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05c8a-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="05c8a-117">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="05c8a-117">listenIPAddress</span></span>|<span data-ttu-id="05c8a-118">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="05c8a-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="05c8a-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-119">The default is `null`.</span></span>|  
|<span data-ttu-id="05c8a-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="05c8a-120">maxBufferPoolSize</span></span>|<span data-ttu-id="05c8a-121">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="05c8a-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="05c8a-122">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="05c8a-123">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="05c8a-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="05c8a-124">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="05c8a-125">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="05c8a-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="05c8a-126">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="05c8a-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="05c8a-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="05c8a-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="05c8a-128">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="05c8a-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="05c8a-129">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="05c8a-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="05c8a-130">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05c8a-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="05c8a-131">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-131">The default is 65536.</span></span>|  
|<span data-ttu-id="05c8a-132">name</span><span class="sxs-lookup"><span data-stu-id="05c8a-132">name</span></span>|<span data-ttu-id="05c8a-133">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="05c8a-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="05c8a-134">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="05c8a-135">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="05c8a-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="05c8a-136">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="05c8a-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="05c8a-137">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="05c8a-137">openTimeout</span></span>|<span data-ttu-id="05c8a-138">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="05c8a-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="05c8a-139">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05c8a-140">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="05c8a-141">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="05c8a-141">port</span></span>|<span data-ttu-id="05c8a-142">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="05c8a-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="05c8a-143">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="05c8a-144">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="05c8a-144">The default is 0.</span></span>|  
|<span data-ttu-id="05c8a-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="05c8a-145">receiveTimeout</span></span>|<span data-ttu-id="05c8a-146">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="05c8a-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="05c8a-147">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05c8a-148">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="05c8a-149">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="05c8a-149">sendTimeout</span></span>|<span data-ttu-id="05c8a-150">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="05c8a-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="05c8a-151">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05c8a-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05c8a-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c8a-153">Child Elements</span></span>  
  
|<span data-ttu-id="05c8a-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="05c8a-154">Element</span></span>|<span data-ttu-id="05c8a-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c8a-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c8a-156">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="05c8a-156">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="05c8a-157">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05c8a-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="05c8a-158">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="05c8a-159">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="05c8a-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="05c8a-160">Uç noktası IP adreslerini eş ağ içindeki düğümler için bir eş çözmek için bu bağlama tarafından kullanılan bir eş çözümleyici ağ Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="05c8a-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="05c8a-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="05c8a-162">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05c8a-162">Defines the security settings for the message.</span></span> <span data-ttu-id="05c8a-163">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="05c8a-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05c8a-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c8a-164">Parent Elements</span></span>  
  
|<span data-ttu-id="05c8a-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="05c8a-165">Element</span></span>|<span data-ttu-id="05c8a-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c8a-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c8a-167">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="05c8a-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="05c8a-168">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="05c8a-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05c8a-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05c8a-169">Remarks</span></span>  
 <span data-ttu-id="05c8a-170">Bu bağlama, TCP üzerinden eş kullanarak eşler arası veya misyonumuz uygulamaların oluşturulması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="05c8a-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="05c8a-171">Her eş düğüm bu bağlama türü tanımlanan birden çok eş kanalı barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05c8a-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05c8a-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="05c8a-172">Example</span></span>  
 <span data-ttu-id="05c8a-173">Aşağıdaki örnek, bir eş kanalı kullanılarak misyonumuz iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="05c8a-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="05c8a-174">Bu bağlama kullanarak ayrıntılı senaryo için bkz. [Net eş TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="05c8a-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a><span data-ttu-id="05c8a-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05c8a-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="05c8a-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="05c8a-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="05c8a-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="05c8a-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="05c8a-178">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="05c8a-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="05c8a-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="05c8a-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="05c8a-180">NET eş TCP</span><span class="sxs-lookup"><span data-stu-id="05c8a-180">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="05c8a-181">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="05c8a-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
