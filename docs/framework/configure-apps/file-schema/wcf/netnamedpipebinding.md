---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: dc1af462222920c7b3c6b66c3822e7b2b326b244
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169831"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="81333-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="81333-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="81333-102">Makinede çapraz proses haberleşmesi için güvenli, güvenilir, bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81333-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="81333-103">Varsayılan olarak, güvenilirlik, aktarım güvenliği ileti teslimi ve ikili ileti kodlama için adlandırılmış kanallar aktarım güvenliği için çalışma zamanı iletişim yığını WS-ReliableMessaging ile oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81333-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="81333-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81333-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81333-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="81333-105">\<bindings></span></span>  
<span data-ttu-id="81333-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="81333-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81333-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81333-107">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81333-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81333-108">Attributes and Elements</span></span>  
 <span data-ttu-id="81333-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81333-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81333-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81333-110">Attributes</span></span>  
  
|<span data-ttu-id="81333-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81333-111">Attribute</span></span>|<span data-ttu-id="81333-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81333-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81333-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="81333-113">closeTimeout</span></span>|<span data-ttu-id="81333-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="81333-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="81333-115">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="81333-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81333-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="81333-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="81333-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="81333-117">hostNameComparisonMode</span></span>|<span data-ttu-id="81333-118">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="81333-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="81333-119">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81333-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="81333-120">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="81333-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="81333-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="81333-121">maxBufferPoolSize</span></span>|<span data-ttu-id="81333-122">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="81333-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="81333-123">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="81333-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="81333-124">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="81333-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="81333-125">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="81333-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="81333-126">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="81333-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="81333-127">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="81333-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="81333-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="81333-128">maxBufferSize</span></span>|<span data-ttu-id="81333-129">Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="81333-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="81333-130">Arabelleği dolu ise, arabellek odası yeniden sahip oluncaya kadar fazlalık veri temel alınan yuvaya kalır.</span><span class="sxs-lookup"><span data-stu-id="81333-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="81333-131">Bu değer olamaz küçüktür `maxReceivedMessageSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="81333-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="81333-132">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="81333-132">The default is 65536.</span></span> <span data-ttu-id="81333-133">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="81333-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="81333-134">MaxConnections</span><span class="sxs-lookup"><span data-stu-id="81333-134">maxConnections</span></span>|<span data-ttu-id="81333-135">En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet oluşturma/kabul eder.</span><span class="sxs-lookup"><span data-stu-id="81333-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="81333-136">Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınırına göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="81333-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="81333-137">Sınırı aşan bir gelen bağlantı sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="81333-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="81333-138">Sınırı aşan giden bağlantılar sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="81333-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="81333-139">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="81333-139">The default is 10.</span></span>|  
|<span data-ttu-id="81333-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="81333-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="81333-141">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="81333-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="81333-142">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="81333-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="81333-143">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81333-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="81333-144">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="81333-144">The default is 65536.</span></span>|  
|<span data-ttu-id="81333-145">name</span><span class="sxs-lookup"><span data-stu-id="81333-145">name</span></span>|<span data-ttu-id="81333-146">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="81333-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="81333-147">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81333-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="81333-148">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="81333-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="81333-149">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="81333-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="81333-150">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="81333-150">openTimeout</span></span>|<span data-ttu-id="81333-151">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="81333-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="81333-152">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="81333-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81333-153">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="81333-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="81333-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="81333-154">receiveTimeout</span></span>|<span data-ttu-id="81333-155">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="81333-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="81333-156">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="81333-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81333-157">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="81333-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="81333-158">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="81333-158">sendTimeout</span></span>|<span data-ttu-id="81333-159">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="81333-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="81333-160">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="81333-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81333-161">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="81333-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="81333-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="81333-162">transactionFlow</span></span>|<span data-ttu-id="81333-163">WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="81333-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="81333-164">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="81333-164">The default is `false`.</span></span>|  
|<span data-ttu-id="81333-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="81333-165">transactionProtocol</span></span>|<span data-ttu-id="81333-166">Bu bağlama ile kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="81333-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="81333-167">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="81333-167">Valid values are</span></span><br /><br /> <span data-ttu-id="81333-168">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="81333-168">-   OleTransactions</span></span><br /><span data-ttu-id="81333-169">-   WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="81333-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="81333-170">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="81333-170">The default is OleTransactions.</span></span> <span data-ttu-id="81333-171">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="81333-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="81333-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="81333-172">transferMode</span></span>|<span data-ttu-id="81333-173">A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="81333-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81333-174">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81333-174">Child Elements</span></span>  
  
|<span data-ttu-id="81333-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="81333-175">Element</span></span>|<span data-ttu-id="81333-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81333-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81333-177">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="81333-177">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="81333-178">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81333-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="81333-179">Bu öğe türünde <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="81333-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="81333-180">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="81333-180">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="81333-181">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81333-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="81333-182">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="81333-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81333-183">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81333-183">Parent Elements</span></span>  
  
|<span data-ttu-id="81333-184">Öğe</span><span class="sxs-lookup"><span data-stu-id="81333-184">Element</span></span>|<span data-ttu-id="81333-185">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81333-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81333-186">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="81333-186">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="81333-187">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="81333-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81333-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81333-188">Remarks</span></span>  
 <span data-ttu-id="81333-189">`NetNamedPipeBinding` Aktarım güvenliği, adlandırılmış kanallar ileti teslimi ve bir ikili ileti kodlama için kullandığı varsayılan bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81333-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="81333-190">Bu bağlama uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanan makinede iletişimi için seçimdir.</span><span class="sxs-lookup"><span data-stu-id="81333-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="81333-191">Ayrıca, işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="81333-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="81333-192">İçin varsayılan yapılandırma `NetNamedPipeBinding` tarafından sağlanan yapılandırma benzer `NetTcpBinding`, ancak bunu WCF uygulaması, yalnızca makinede kullanılmak üzere tasarlanmıştır ve bu nedenle daha az sunulan özellikler vardır çünkü daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="81333-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="81333-193">En önemli fark `securityMode` yalnızca teklifler ayarlama `None` ve `Transport` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="81333-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="81333-194">SOAP güvenlik desteği, dahil edilen bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="81333-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="81333-195">Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="81333-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81333-196">Örnek</span><span class="sxs-lookup"><span data-stu-id="81333-196">Example</span></span>  
 <span data-ttu-id="81333-197">Aşağıdaki örnek, aynı makinede çapraz proses haberleşmesi sağlayan netNamedPipeBinding bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="81333-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="81333-198">Adlandırılmış Kanallar makinelerde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="81333-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="81333-199">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="81333-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="81333-200">Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="81333-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="81333-201">NetNamedPipeBinding yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81333-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="81333-202">Uç nokta adı ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="81333-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="81333-203">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="81333-203">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="81333-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81333-204">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="81333-205">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81333-205">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="81333-206">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81333-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="81333-207">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81333-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81333-208">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="81333-208">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
