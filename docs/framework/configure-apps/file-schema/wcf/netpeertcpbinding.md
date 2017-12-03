---
title: '&lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35dfb3eee5a01d5fed21bda59f1cab5eb09a1401
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="d3486-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d3486-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="d3486-103">Eş kanal belirli TCP ileti için bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3486-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="d3486-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d3486-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3486-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d3486-105">\<bindings></span></span>  
<span data-ttu-id="d3486-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d3486-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3486-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3486-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3486-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3486-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d3486-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="d3486-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3486-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3486-110">Attributes</span></span>  
  
|<span data-ttu-id="d3486-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3486-111">Attribute</span></span>|<span data-ttu-id="d3486-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3486-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3486-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d3486-113">closeTimeout</span></span>|<span data-ttu-id="d3486-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d3486-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d3486-115">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3486-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3486-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3486-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d3486-117">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="d3486-117">listenIPAddress</span></span>|<span data-ttu-id="d3486-118">Eş düğüm için TCP iletileri dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d3486-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="d3486-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d3486-119">The default is `null`.</span></span>|  
|<span data-ttu-id="d3486-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d3486-120">maxBufferPoolSize</span></span>|<span data-ttu-id="d3486-121">Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3486-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d3486-122">Varsayılan 524.288 (512 * 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="d3486-122">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="d3486-123">Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3486-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d3486-124">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3486-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d3486-125">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="d3486-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d3486-126">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="d3486-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d3486-127">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d3486-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="d3486-128">Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3486-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d3486-129">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="d3486-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="d3486-130">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3486-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d3486-131">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d3486-131">The default is 65536.</span></span>|  
|<span data-ttu-id="d3486-132">name</span><span class="sxs-lookup"><span data-stu-id="d3486-132">name</span></span>|<span data-ttu-id="d3486-133">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="d3486-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d3486-134">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3486-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d3486-135">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d3486-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d3486-136">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d3486-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="d3486-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d3486-137">openTimeout</span></span>|<span data-ttu-id="d3486-138">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d3486-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d3486-139">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3486-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3486-140">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3486-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d3486-141">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="d3486-141">port</span></span>|<span data-ttu-id="d3486-142">Bu bağlama eş kanal TCP iletilerini işleyecek ağ arabirim bağlantı noktası belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3486-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="d3486-143">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="d3486-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="d3486-144">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="d3486-144">The default is 0.</span></span>|  
|<span data-ttu-id="d3486-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d3486-145">receiveTimeout</span></span>|<span data-ttu-id="d3486-146">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d3486-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d3486-147">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3486-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3486-148">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="d3486-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="d3486-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="d3486-149">sendTimeout</span></span>|<span data-ttu-id="d3486-150">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d3486-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d3486-151">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3486-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3486-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3486-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3486-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3486-153">Child Elements</span></span>  
  
|<span data-ttu-id="d3486-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3486-154">Element</span></span>|<span data-ttu-id="d3486-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3486-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3486-156">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="d3486-156">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="d3486-157">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3486-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d3486-158">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d3486-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="d3486-159">\<Çözümleyici ></span><span class="sxs-lookup"><span data-stu-id="d3486-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="d3486-160">Bir eş çözümlemek için bu bağlama tarafından kullanılan bir eş çözümleyici uç noktası IP adreslerini eş kafes içindeki düğümler için kimliği kafes belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3486-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="d3486-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d3486-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="d3486-162">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3486-162">Defines the security settings for the message.</span></span> <span data-ttu-id="d3486-163">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d3486-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3486-164">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3486-164">Parent Elements</span></span>  
  
|<span data-ttu-id="d3486-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3486-165">Element</span></span>|<span data-ttu-id="d3486-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3486-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3486-167">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d3486-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="d3486-168">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d3486-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3486-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3486-169">Remarks</span></span>  
 <span data-ttu-id="d3486-170">Bu bağlama, TCP üzerinden eş aktarım kullanılarak eşler arası veya çok taraflı uygulamalarının oluşturulması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3486-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="d3486-171">Her eş düğüm bu bağlama türü ile tanımlanmış birden çok eş kanalı barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="d3486-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3486-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3486-172">Example</span></span>  
 <span data-ttu-id="d3486-173">Aşağıdaki örnek, bir eş kanalı kullanılarak taraflı iletişimi sağlayan NetPeerTcpBinding bağlama kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3486-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="d3486-174">Bu bağlama işlemini kullanma ayrıntılı senaryo için bkz [Net eş TCP](http://msdn.microsoft.com/en-us/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="d3486-174">For a detailed scenario of using this binding, see [Net Peer TCP](http://msdn.microsoft.com/en-us/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3486-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3486-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="d3486-176">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="d3486-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d3486-177">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d3486-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d3486-178">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d3486-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d3486-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d3486-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="d3486-180">NET eş TCP</span><span class="sxs-lookup"><span data-stu-id="d3486-180">Net Peer TCP</span></span>](http://msdn.microsoft.com/en-us/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="d3486-181">Eşler arası ağ</span><span class="sxs-lookup"><span data-stu-id="d3486-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
