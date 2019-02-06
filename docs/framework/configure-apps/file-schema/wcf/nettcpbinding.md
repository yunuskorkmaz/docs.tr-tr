---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 54e9a488b9e83b07d1d6d7e18e92ecedc5c74ea6
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759190"
---
# <a name="nettcpbinding"></a><span data-ttu-id="56bd2-101">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="56bd2-101">\<netTcpBinding></span></span>

<span data-ttu-id="56bd2-102">Çapraz makine haberleşmesi için güvenli, güvenilir ve iyileştirilmiş bağlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="56bd2-103">Varsayılan olarak, bir çalışma zamanı iletişim yığını Windows güvenliği ile ileti güvenliği ve kimlik doğrulaması, ileti teslimi ve ikili ileti kodlama için TCP oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="56bd2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56bd2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="56bd2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="56bd2-105">\<bindings></span></span>  
<span data-ttu-id="56bd2-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="56bd2-106">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56bd2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56bd2-107">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56bd2-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="56bd2-108">Attributes and elements</span></span>

<span data-ttu-id="56bd2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56bd2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56bd2-110">Attributes</span></span>  
  
|<span data-ttu-id="56bd2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="56bd2-111">Attribute</span></span>|<span data-ttu-id="56bd2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56bd2-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="56bd2-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="56bd2-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="56bd2-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="56bd2-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-115">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="56bd2-116">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="56bd2-117">Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-117">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="56bd2-118">Varsayılan değer `StrongWildcard`, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="56bd2-118">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="56bd2-119">En fazla kabul edilmesi için Dinleyicide bekleyen kanal sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="56bd2-119">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="56bd2-120">Bu sınırı aşan bağlantılar, sınırın altına alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-120">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="56bd2-121">`connectionTimeout` Öznitelik, bir istemci, bağlantı özel durumuyla atamadan önce bağlanması için bekleyeceği süre sınırlar.</span><span class="sxs-lookup"><span data-stu-id="56bd2-121">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="56bd2-122">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-122">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="56bd2-123">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="56bd2-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="56bd2-124">Varsayılan değer 512 \* 1024 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-124">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="56bd2-125">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="56bd2-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="56bd2-126">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="56bd2-127">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="56bd2-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="56bd2-128">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="56bd2-129">Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="56bd2-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="56bd2-130">Varsa `transferMode` özniteliği eşittir için `Buffered`, bu öznitelik eşit olmalıdır `maxReceivedMessageSize` öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="56bd2-130">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="56bd2-131">Varsa `transferMode` özniteliği eşittir için `Streamed`, bu öznitelik birden fazla `maxReceivedMessageSize` öznitelik değeri ve üst bilgilerin boyutu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-131">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="56bd2-132">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-132">The default is 65536.</span></span> <span data-ttu-id="56bd2-133">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="56bd2-134">En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet oluşturma/kabul eder.</span><span class="sxs-lookup"><span data-stu-id="56bd2-134">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="56bd2-135">Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınırına göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-135">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="56bd2-136">Sınırı aşan bir gelen bağlantı sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-136">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="56bd2-137">Sınırı aşan giden bağlantılar sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-137">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="56bd2-138">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-138">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="56bd2-139">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="56bd2-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="56bd2-140">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="56bd2-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="56bd2-141">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="56bd2-142">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-142">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="56bd2-143">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="56bd2-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="56bd2-144">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="56bd2-145">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="56bd2-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="56bd2-146">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="56bd2-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="56bd2-147">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="56bd2-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="56bd2-148">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="56bd2-149">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-149">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="56bd2-150">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="56bd2-150">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="56bd2-151">Bu ise `false`, her bir bağlaması, kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-151">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="56bd2-152">Bu ayar yalnızca hizmetler için ilgili çünkü istemciler etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="56bd2-152">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="56bd2-153">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="56bd2-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="56bd2-154">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="56bd2-155">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-155">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="56bd2-156">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="56bd2-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="56bd2-157">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="56bd2-158">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-158">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="56bd2-159">WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="56bd2-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="56bd2-160">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-160">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="56bd2-161">Bu bağlama ile kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="56bd2-161">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="56bd2-162">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="56bd2-162">Valid values are</span></span><br /><br /> <span data-ttu-id="56bd2-163">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="56bd2-163">-   OleTransactions</span></span><br /><span data-ttu-id="56bd2-164">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="56bd2-164">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="56bd2-165">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-165">The default is OleTransactions.</span></span> <span data-ttu-id="56bd2-166">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-166">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="56bd2-167">A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="56bd2-167">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56bd2-168">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="56bd2-168">Child elements</span></span>  
  
|<span data-ttu-id="56bd2-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="56bd2-169">Element</span></span>|<span data-ttu-id="56bd2-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56bd2-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56bd2-171">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="56bd2-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="56bd2-172">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56bd2-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="56bd2-173">Bu öğe türünde <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-173">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="56bd2-174">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="56bd2-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="56bd2-175">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56bd2-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="56bd2-176">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="56bd2-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="56bd2-177">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="56bd2-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="56bd2-178">Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-178">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56bd2-179">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="56bd2-179">Parent elements</span></span>  
  
|<span data-ttu-id="56bd2-180">Öğe</span><span class="sxs-lookup"><span data-stu-id="56bd2-180">Element</span></span>|<span data-ttu-id="56bd2-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56bd2-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56bd2-182">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="56bd2-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="56bd2-183">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="56bd2-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56bd2-184">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56bd2-184">Remarks</span></span>

<span data-ttu-id="56bd2-185">Bu bağlama, aktarım güvenliği, ileti teslimi için TCP ve bir ikili ileti kodlama kullanan varsayılan olarak, bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56bd2-185">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="56bd2-186">Bu bağlama Intranet üzerinden iletişim için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanan seçimdir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-186">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="56bd2-187">İçin varsayılan yapılandırma `netTcpBinding` tarafından sağlanan yapılandırma daha hızlıdır `wsHttpBinding`, ancak yalnızca WCF iletişim için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-187">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="56bd2-188">Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="56bd2-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="56bd2-189">İsteğe bağlı kullanılarak yapılandırılabilir WS-ReliableMessaging kullanımını `reliableSessionEnabled` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="56bd2-189">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="56bd2-190">Ancak, güvenilir Mesajlaşma varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-190">But reliable messaging is off by default.</span></span> <span data-ttu-id="56bd2-191">Daha genel HTTP sistem tarafından sağlanan bağlamalar gibi `wsHttpBinding` ve `basicHttpBinding` öğeleri varsayılan olarak, açmak için ise yapılandırılmış `netTcpBinding` bağlama kapanmadan öğeleri varsayılan olarak biri için destek, örneğin, alma katılımı sahip WS-\* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="56bd2-191">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="56bd2-192">Bu, TCP için varsayılan yapılandırma varsayılan olarak HTTP bağlantıları için yapılandırılan daha uç noktalar arasında mesaj alışverişleri sırasında daha hızlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-192">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56bd2-193">Örnek</span><span class="sxs-lookup"><span data-stu-id="56bd2-193">Example</span></span>

<span data-ttu-id="56bd2-194">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="56bd2-194">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="56bd2-195">Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="56bd2-195">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="56bd2-196">NetTcpBinding yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="56bd2-196">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="56bd2-197">Uç nokta ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="56bd2-197">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="56bd2-198">Aşağıdaki örnekte, bir bağlama yapılandırmasını tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="56bd2-198">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="56bd2-199">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56bd2-199">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="56bd2-200">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="56bd2-200">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="56bd2-201">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56bd2-201">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="56bd2-202">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="56bd2-202">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="56bd2-203">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="56bd2-203">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
