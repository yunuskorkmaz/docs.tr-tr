---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: b35e2f365e82291d3f8b827850fdebfe8fa2237d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780373"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="819a7-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="819a7-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="819a7-102">Eş kanallı belirli TCP Mesajlaşma için bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="819a7-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="819a7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="819a7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="819a7-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="819a7-104">\<bindings></span></span>  
<span data-ttu-id="819a7-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="819a7-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="819a7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="819a7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="819a7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="819a7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="819a7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="819a7-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="819a7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="819a7-109">Attributes</span></span>  
  
|<span data-ttu-id="819a7-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="819a7-110">Attribute</span></span>|<span data-ttu-id="819a7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="819a7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="819a7-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="819a7-112">closeTimeout</span></span>|<span data-ttu-id="819a7-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="819a7-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="819a7-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="819a7-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="819a7-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="819a7-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="819a7-116">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="819a7-116">listenIPAddress</span></span>|<span data-ttu-id="819a7-117">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="819a7-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="819a7-118">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="819a7-118">The default is `null`.</span></span>|  
|<span data-ttu-id="819a7-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="819a7-119">maxBufferPoolSize</span></span>|<span data-ttu-id="819a7-120">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="819a7-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="819a7-121">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="819a7-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="819a7-122">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="819a7-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="819a7-123">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="819a7-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="819a7-124">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="819a7-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="819a7-125">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="819a7-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="819a7-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="819a7-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="819a7-127">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="819a7-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="819a7-128">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="819a7-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="819a7-129">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="819a7-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="819a7-130">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="819a7-130">The default is 65536.</span></span>|  
|<span data-ttu-id="819a7-131">name</span><span class="sxs-lookup"><span data-stu-id="819a7-131">name</span></span>|<span data-ttu-id="819a7-132">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="819a7-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="819a7-133">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="819a7-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="819a7-134">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="819a7-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="819a7-135">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="819a7-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="819a7-136">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="819a7-136">openTimeout</span></span>|<span data-ttu-id="819a7-137">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="819a7-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="819a7-138">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="819a7-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="819a7-139">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="819a7-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="819a7-140">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="819a7-140">port</span></span>|<span data-ttu-id="819a7-141">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="819a7-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="819a7-142">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="819a7-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="819a7-143">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="819a7-143">The default is 0.</span></span>|  
|<span data-ttu-id="819a7-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="819a7-144">receiveTimeout</span></span>|<span data-ttu-id="819a7-145">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="819a7-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="819a7-146">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="819a7-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="819a7-147">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="819a7-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="819a7-148">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="819a7-148">sendTimeout</span></span>|<span data-ttu-id="819a7-149">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="819a7-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="819a7-150">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="819a7-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="819a7-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="819a7-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="819a7-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="819a7-152">Child Elements</span></span>  
  
|<span data-ttu-id="819a7-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="819a7-153">Element</span></span>|<span data-ttu-id="819a7-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="819a7-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="819a7-155">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="819a7-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="819a7-156">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="819a7-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="819a7-157">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="819a7-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="819a7-158">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="819a7-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="819a7-159">Uç noktası IP adreslerini eş ağ içindeki düğümler için bir eş çözmek için bu bağlama tarafından kullanılan bir eş çözümleyici ağ Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="819a7-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="819a7-160">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="819a7-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="819a7-161">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="819a7-161">Defines the security settings for the message.</span></span> <span data-ttu-id="819a7-162">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="819a7-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="819a7-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="819a7-163">Parent Elements</span></span>  
  
|<span data-ttu-id="819a7-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="819a7-164">Element</span></span>|<span data-ttu-id="819a7-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="819a7-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="819a7-166">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="819a7-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="819a7-167">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="819a7-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="819a7-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="819a7-168">Remarks</span></span>  
 <span data-ttu-id="819a7-169">Bu bağlama, TCP üzerinden eş kullanarak eşler arası veya misyonumuz uygulamaların oluşturulması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="819a7-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="819a7-170">Her eş düğüm bu bağlama türü tanımlanan birden çok eş kanalı barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="819a7-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819a7-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="819a7-171">Example</span></span>  
 <span data-ttu-id="819a7-172">Aşağıdaki örnek, bir eş kanalı kullanılarak misyonumuz iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="819a7-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="819a7-173">Bu bağlama kullanarak ayrıntılı senaryo için bkz. [Net eş TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="819a7-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="819a7-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="819a7-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="819a7-175">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="819a7-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="819a7-176">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="819a7-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="819a7-177">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="819a7-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="819a7-178">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="819a7-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- <span data-ttu-id="819a7-179">[NET eş TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="819a7-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="819a7-180">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="819a7-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
