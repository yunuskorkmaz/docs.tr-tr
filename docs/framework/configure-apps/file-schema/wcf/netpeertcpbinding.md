---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: a039e805bc4378582d7a7bcf6ef84591ec3d2b6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261444"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="8d604-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8d604-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="8d604-102">Eş kanallı belirli TCP Mesajlaşma için bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d604-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="8d604-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8d604-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d604-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8d604-104">\<bindings></span></span>  
<span data-ttu-id="8d604-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8d604-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d604-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d604-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d604-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d604-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8d604-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d604-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d604-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d604-109">Attributes</span></span>  
  
|<span data-ttu-id="8d604-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8d604-110">Attribute</span></span>|<span data-ttu-id="8d604-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d604-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d604-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="8d604-112">closeTimeout</span></span>|<span data-ttu-id="8d604-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8d604-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8d604-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8d604-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8d604-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d604-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="8d604-116">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="8d604-116">listenIPAddress</span></span>|<span data-ttu-id="8d604-117">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d604-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="8d604-118">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8d604-118">The default is `null`.</span></span>|  
|<span data-ttu-id="8d604-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8d604-119">maxBufferPoolSize</span></span>|<span data-ttu-id="8d604-120">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8d604-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="8d604-121">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="8d604-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="8d604-122">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d604-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="8d604-123">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d604-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8d604-124">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="8d604-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8d604-125">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="8d604-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="8d604-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8d604-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="8d604-127">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8d604-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="8d604-128">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="8d604-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="8d604-129">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d604-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8d604-130">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="8d604-130">The default is 65536.</span></span>|  
|<span data-ttu-id="8d604-131">name</span><span class="sxs-lookup"><span data-stu-id="8d604-131">name</span></span>|<span data-ttu-id="8d604-132">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d604-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8d604-133">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d604-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8d604-134">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="8d604-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8d604-135">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8d604-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="8d604-136">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="8d604-136">openTimeout</span></span>|<span data-ttu-id="8d604-137">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8d604-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8d604-138">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8d604-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8d604-139">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d604-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="8d604-140">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="8d604-140">port</span></span>|<span data-ttu-id="8d604-141">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8d604-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="8d604-142">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="8d604-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="8d604-143">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="8d604-143">The default is 0.</span></span>|  
|<span data-ttu-id="8d604-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="8d604-144">receiveTimeout</span></span>|<span data-ttu-id="8d604-145">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8d604-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8d604-146">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8d604-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8d604-147">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d604-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="8d604-148">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="8d604-148">sendTimeout</span></span>|<span data-ttu-id="8d604-149">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8d604-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8d604-150">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="8d604-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8d604-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d604-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d604-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d604-152">Child Elements</span></span>  
  
|<span data-ttu-id="8d604-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d604-153">Element</span></span>|<span data-ttu-id="8d604-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d604-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d604-155">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="8d604-155">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="8d604-156">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d604-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8d604-157">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8d604-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="8d604-158">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="8d604-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="8d604-159">Uç noktası IP adreslerini eş ağ içindeki düğümler için bir eş çözmek için bu bağlama tarafından kullanılan bir eş çözümleyici ağ Kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d604-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="8d604-160">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="8d604-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="8d604-161">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d604-161">Defines the security settings for the message.</span></span> <span data-ttu-id="8d604-162">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8d604-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d604-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d604-163">Parent Elements</span></span>  
  
|<span data-ttu-id="8d604-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d604-164">Element</span></span>|<span data-ttu-id="8d604-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d604-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d604-166">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8d604-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="8d604-167">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="8d604-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d604-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d604-168">Remarks</span></span>  
 <span data-ttu-id="8d604-169">Bu bağlama, TCP üzerinden eş kullanarak eşler arası veya misyonumuz uygulamaların oluşturulması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d604-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="8d604-170">Her eş düğüm bu bağlama türü tanımlanan birden çok eş kanalı barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d604-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d604-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d604-171">Example</span></span>  
 <span data-ttu-id="8d604-172">Aşağıdaki örnek, bir eş kanalı kullanılarak misyonumuz iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d604-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="8d604-173">Bu bağlama kullanarak ayrıntılı senaryo için bkz. [Net eş TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="8d604-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d604-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d604-174">See also</span></span>
- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="8d604-175">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8d604-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8d604-176">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d604-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8d604-177">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8d604-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8d604-178">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8d604-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="8d604-179">NET eş TCP</span><span class="sxs-lookup"><span data-stu-id="8d604-179">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)
- [<span data-ttu-id="8d604-180">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="8d604-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
