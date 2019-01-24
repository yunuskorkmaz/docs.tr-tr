---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 045d5649ae7f59087eacd035d7be09d0024b6fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725668"
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="baece-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="baece-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="baece-103">Eş kanallı belirli TCP Mesajlaşma için bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="baece-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="baece-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="baece-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="baece-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="baece-105">\<bindings></span></span>  
<span data-ttu-id="baece-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="baece-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baece-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baece-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baece-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="baece-108">Attributes and Elements</span></span>  
 <span data-ttu-id="baece-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="baece-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baece-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="baece-110">Attributes</span></span>  
  
|<span data-ttu-id="baece-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="baece-111">Attribute</span></span>|<span data-ttu-id="baece-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baece-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baece-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="baece-113">closeTimeout</span></span>|<span data-ttu-id="baece-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="baece-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="baece-115">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="baece-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="baece-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="baece-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="baece-117">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="baece-117">listenIPAddress</span></span>|<span data-ttu-id="baece-118">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="baece-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="baece-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="baece-119">The default is `null`.</span></span>|  
|<span data-ttu-id="baece-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="baece-120">maxBufferPoolSize</span></span>|<span data-ttu-id="baece-121">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="baece-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="baece-122">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="baece-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="baece-123">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="baece-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="baece-124">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="baece-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="baece-125">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="baece-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="baece-126">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="baece-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="baece-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="baece-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="baece-128">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="baece-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="baece-129">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="baece-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="baece-130">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="baece-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="baece-131">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="baece-131">The default is 65536.</span></span>|  
|<span data-ttu-id="baece-132">name</span><span class="sxs-lookup"><span data-stu-id="baece-132">name</span></span>|<span data-ttu-id="baece-133">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="baece-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="baece-134">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="baece-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="baece-135">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="baece-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="baece-136">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="baece-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="baece-137">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="baece-137">openTimeout</span></span>|<span data-ttu-id="baece-138">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="baece-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="baece-139">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="baece-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="baece-140">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="baece-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="baece-141">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="baece-141">port</span></span>|<span data-ttu-id="baece-142">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="baece-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="baece-143">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="baece-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="baece-144">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="baece-144">The default is 0.</span></span>|  
|<span data-ttu-id="baece-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="baece-145">receiveTimeout</span></span>|<span data-ttu-id="baece-146">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="baece-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="baece-147">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="baece-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="baece-148">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="baece-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="baece-149">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="baece-149">sendTimeout</span></span>|<span data-ttu-id="baece-150">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="baece-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="baece-151">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="baece-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="baece-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="baece-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baece-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="baece-153">Child Elements</span></span>  
  
|<span data-ttu-id="baece-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="baece-154">Element</span></span>|<span data-ttu-id="baece-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baece-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baece-156">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="baece-156">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="baece-157">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="baece-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="baece-158">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="baece-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="baece-159">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="baece-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="baece-160">Uç noktası IP adreslerini eş ağ içindeki düğümler için bir eş çözmek için bu bağlama tarafından kullanılan bir eş çözümleyici ağ Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baece-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="baece-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="baece-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="baece-162">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="baece-162">Defines the security settings for the message.</span></span> <span data-ttu-id="baece-163">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="baece-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="baece-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="baece-164">Parent Elements</span></span>  
  
|<span data-ttu-id="baece-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="baece-165">Element</span></span>|<span data-ttu-id="baece-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baece-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baece-167">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="baece-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="baece-168">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="baece-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baece-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baece-169">Remarks</span></span>  
 <span data-ttu-id="baece-170">Bu bağlama, TCP üzerinden eş kullanarak eşler arası veya misyonumuz uygulamaların oluşturulması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="baece-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="baece-171">Her eş düğüm bu bağlama türü tanımlanan birden çok eş kanalı barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baece-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baece-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="baece-172">Example</span></span>  
 <span data-ttu-id="baece-173">Aşağıdaki örnek, bir eş kanalı kullanılarak misyonumuz iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="baece-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="baece-174">Bu bağlama kullanarak ayrıntılı senaryo için bkz. [Net eş TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="baece-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="baece-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baece-175">See also</span></span>
- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="baece-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="baece-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="baece-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="baece-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="baece-178">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="baece-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="baece-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="baece-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="baece-180">NET eş TCP</span><span class="sxs-lookup"><span data-stu-id="baece-180">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)
- [<span data-ttu-id="baece-181">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="baece-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
