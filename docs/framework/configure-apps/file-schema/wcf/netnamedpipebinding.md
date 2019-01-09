---
title: '&lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 545148d1f663078b8182029817f0f22d33036200
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152040"
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="457c7-102">&lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="457c7-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="457c7-103">Makinede çapraz proses haberleşmesi için güvenli, güvenilir, bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="457c7-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="457c7-104">Varsayılan olarak, güvenilirlik, aktarım güvenliği ileti teslimi ve ikili ileti kodlama için adlandırılmış kanallar aktarım güvenliği için çalışma zamanı iletişim yığını WS-ReliableMessaging ile oluşturur.</span><span class="sxs-lookup"><span data-stu-id="457c7-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="457c7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="457c7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="457c7-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="457c7-106">\<bindings></span></span>  
<span data-ttu-id="457c7-107">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="457c7-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457c7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="457c7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="457c7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="457c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="457c7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="457c7-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="457c7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="457c7-111">Attributes</span></span>  
  
|<span data-ttu-id="457c7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="457c7-112">Attribute</span></span>|<span data-ttu-id="457c7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457c7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="457c7-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="457c7-114">closeTimeout</span></span>|<span data-ttu-id="457c7-115">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="457c7-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="457c7-116">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="457c7-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="457c7-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="457c7-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="457c7-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="457c7-118">hostnameComparisonMode</span></span>|<span data-ttu-id="457c7-119">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="457c7-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="457c7-120">Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="457c7-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="457c7-121">Varsayılan değer `StrongWildcard`, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="457c7-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="457c7-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="457c7-122">maxBufferPoolSize</span></span>|<span data-ttu-id="457c7-123">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="457c7-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="457c7-124">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="457c7-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="457c7-125">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="457c7-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="457c7-126">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="457c7-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="457c7-127">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="457c7-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="457c7-128">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="457c7-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="457c7-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="457c7-129">maxBufferSize</span></span>|<span data-ttu-id="457c7-130">Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="457c7-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="457c7-131">Arabelleği dolu ise, arabellek odası yeniden sahip oluncaya kadar fazlalık veri temel alınan yuvaya kalır.</span><span class="sxs-lookup"><span data-stu-id="457c7-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="457c7-132">Bu değer olamaz küçüktür `maxReceivedMessageSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="457c7-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="457c7-133">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="457c7-133">The default is 65536.</span></span> <span data-ttu-id="457c7-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="457c7-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="457c7-135">MaxConnections</span><span class="sxs-lookup"><span data-stu-id="457c7-135">maxConnections</span></span>|<span data-ttu-id="457c7-136">En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet oluşturma/kabul eder.</span><span class="sxs-lookup"><span data-stu-id="457c7-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="457c7-137">Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınırına göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="457c7-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="457c7-138">Sınırı aşan bir gelen bağlantı sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="457c7-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="457c7-139">Sınırı aşan giden bağlantılar sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="457c7-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="457c7-140">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="457c7-140">The default is 10.</span></span>|  
|<span data-ttu-id="457c7-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="457c7-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="457c7-142">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="457c7-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="457c7-143">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="457c7-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="457c7-144">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="457c7-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="457c7-145">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="457c7-145">The default is 65536.</span></span>|  
|<span data-ttu-id="457c7-146">name</span><span class="sxs-lookup"><span data-stu-id="457c7-146">name</span></span>|<span data-ttu-id="457c7-147">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="457c7-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="457c7-148">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="457c7-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="457c7-149">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="457c7-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="457c7-150">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="457c7-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="457c7-151">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="457c7-151">openTimeout</span></span>|<span data-ttu-id="457c7-152">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="457c7-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="457c7-153">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="457c7-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="457c7-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="457c7-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="457c7-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="457c7-155">receiveTimeout</span></span>|<span data-ttu-id="457c7-156">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="457c7-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="457c7-157">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="457c7-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="457c7-158">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="457c7-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="457c7-159">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="457c7-159">sendTimeout</span></span>|<span data-ttu-id="457c7-160">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="457c7-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="457c7-161">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="457c7-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="457c7-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="457c7-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="457c7-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="457c7-163">transactionFlow</span></span>|<span data-ttu-id="457c7-164">WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="457c7-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="457c7-165">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="457c7-165">The default is `false`.</span></span>|  
|<span data-ttu-id="457c7-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="457c7-166">transactionProtocol</span></span>|<span data-ttu-id="457c7-167">Bu bağlama ile kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="457c7-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="457c7-168">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="457c7-168">Valid values are</span></span><br /><br /> <span data-ttu-id="457c7-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="457c7-169">-   OleTransactions</span></span><br /><span data-ttu-id="457c7-170">WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="457c7-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="457c7-171">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="457c7-171">The default is OleTransactions.</span></span> <span data-ttu-id="457c7-172">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="457c7-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="457c7-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="457c7-173">transferMode</span></span>|<span data-ttu-id="457c7-174">A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten bir değer veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="457c7-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="457c7-175">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="457c7-175">Child Elements</span></span>  
  
|<span data-ttu-id="457c7-176">Öğe</span><span class="sxs-lookup"><span data-stu-id="457c7-176">Element</span></span>|<span data-ttu-id="457c7-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457c7-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="457c7-178">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="457c7-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="457c7-179">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="457c7-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="457c7-180">Bu öğe türünde <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="457c7-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="457c7-181">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="457c7-181">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="457c7-182">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="457c7-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="457c7-183">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="457c7-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="457c7-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="457c7-184">Parent Elements</span></span>  
  
|<span data-ttu-id="457c7-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="457c7-185">Element</span></span>|<span data-ttu-id="457c7-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="457c7-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="457c7-187">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="457c7-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="457c7-188">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="457c7-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="457c7-189">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="457c7-189">Remarks</span></span>  
 <span data-ttu-id="457c7-190">`NetNamedPipeBinding` Aktarım güvenliği, adlandırılmış kanallar ileti teslimi ve bir ikili ileti kodlama için kullandığı varsayılan bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="457c7-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="457c7-191">Bu bağlama uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanan makinede iletişimi için seçimdir.</span><span class="sxs-lookup"><span data-stu-id="457c7-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="457c7-192">Ayrıca, işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="457c7-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="457c7-193">İçin varsayılan yapılandırma `NetNamedPipeBinding` tarafından sağlanan yapılandırma benzer `NetTcpBinding`, ancak bunu WCF uygulaması, yalnızca makinede kullanılmak üzere tasarlanmıştır ve bu nedenle daha az sunulan özellikler vardır çünkü daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="457c7-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="457c7-194">En önemli fark `securityMode` yalnızca teklifler ayarlama `None` ve `Transport` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="457c7-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="457c7-195">SOAP güvenlik desteği, dahil edilen bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="457c7-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="457c7-196">Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="457c7-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="457c7-197">Örnek</span><span class="sxs-lookup"><span data-stu-id="457c7-197">Example</span></span>  
 <span data-ttu-id="457c7-198">Aşağıdaki örnek, aynı makinede çapraz proses haberleşmesi sağlayan netNamedPipeBinding bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="457c7-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="457c7-199">Adlandırılmış Kanallar makinelerde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="457c7-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="457c7-200">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="457c7-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="457c7-201">Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="457c7-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="457c7-202">NetNamedPipeBinding yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="457c7-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="457c7-203">Uç nokta adı ile bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="457c7-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="457c7-204">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="457c7-204">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="457c7-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="457c7-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="457c7-206">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="457c7-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="457c7-207">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="457c7-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="457c7-208">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="457c7-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="457c7-209">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="457c7-209">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
