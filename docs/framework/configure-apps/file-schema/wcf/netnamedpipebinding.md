---
title: '&lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f5bf4a933928770744e8974b5bb20ef06f18c93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="1bdc8-102">&lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1bdc8-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="1bdc8-103">Güvenli, güvenilir, üzerinde-makine çapraz işlem iletişim için en iyi hale getirilmiş bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="1bdc8-104">Varsayılan olarak, güvenilirlik, ileti teslimi ve ikili ileti kodlama için adlandırılmış kanallar aktarımı güvenlik için taşıma güvenliği için çalışma zamanı iletişim yığını WS-ReliableMessaging ile oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="1bdc8-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1bdc8-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-106">\<bindings></span></span>  
<span data-ttu-id="1bdc8-107">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdc8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bdc8-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bdc8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bdc8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1bdc8-110">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="1bdc8-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bdc8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bdc8-111">Attributes</span></span>  
  
|<span data-ttu-id="1bdc8-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1bdc8-112">Attribute</span></span>|<span data-ttu-id="1bdc8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bdc8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1bdc8-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="1bdc8-114">closeTimeout</span></span>|<span data-ttu-id="1bdc8-115">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1bdc8-116">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1bdc8-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1bdc8-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="1bdc8-118">hostnameComparisonMode</span></span>|<span data-ttu-id="1bdc8-119">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1bdc8-120">Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1bdc8-121">Varsayılan değer `StrongWildcard`, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="1bdc8-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1bdc8-122">maxBufferPoolSize</span></span>|<span data-ttu-id="1bdc8-123">Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1bdc8-124">Varsayılan 524.288 (512 * 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-124">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="1bdc8-125">Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1bdc8-126">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1bdc8-127">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1bdc8-128">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="1bdc8-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="1bdc8-129">maxBufferSize</span></span>|<span data-ttu-id="1bdc8-130">Bellekte iletileri depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="1bdc8-131">Arabellek dolu ise, arabellek yeniden yer olana kadar aşırı verileri temel alınan bir yuvada kalır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="1bdc8-132">Bu değer olamaz değerinden `maxReceivedMessageSize` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="1bdc8-133">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-133">The default is 65536.</span></span> <span data-ttu-id="1bdc8-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="1bdc8-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="1bdc8-135">maxConnections</span></span>|<span data-ttu-id="1bdc8-136">En fazla giden ve gelen bağlantı sayısını belirten bir tamsayı hizmet Oluştur/kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="1bdc8-137">Gelen ve giden bağlantılar bu özniteliği tarafından belirtilen ayrı bir sınır karşı sayılır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="1bdc8-138">Sınırı aşan gelen bağlantıları sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="1bdc8-139">Sınırı aşan giden bağlantılar sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="1bdc8-140">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-140">The default is 10.</span></span>|  
|<span data-ttu-id="1bdc8-141">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1bdc8-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="1bdc8-142">Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1bdc8-143">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="1bdc8-144">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1bdc8-145">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-145">The default is 65536.</span></span>|  
|<span data-ttu-id="1bdc8-146">name</span><span class="sxs-lookup"><span data-stu-id="1bdc8-146">name</span></span>|<span data-ttu-id="1bdc8-147">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1bdc8-148">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1bdc8-149">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1bdc8-150">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1bdc8-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="1bdc8-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="1bdc8-151">openTimeout</span></span>|<span data-ttu-id="1bdc8-152">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1bdc8-153">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1bdc8-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1bdc8-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="1bdc8-155">receiveTimeout</span></span>|<span data-ttu-id="1bdc8-156">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1bdc8-157">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1bdc8-158">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="1bdc8-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="1bdc8-159">sendTimeout</span></span>|<span data-ttu-id="1bdc8-160">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1bdc8-161">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1bdc8-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1bdc8-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="1bdc8-163">transactionFlow</span></span>|<span data-ttu-id="1bdc8-164">Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="1bdc8-165">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-165">The default is `false`.</span></span>|  
|<span data-ttu-id="1bdc8-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="1bdc8-166">transactionProtocol</span></span>|<span data-ttu-id="1bdc8-167">Bu bağlama ile kullanılmak üzere işlem protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="1bdc8-168">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="1bdc8-168">Valid values are</span></span><br /><br /> <span data-ttu-id="1bdc8-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1bdc8-169">-   OleTransactions</span></span><br /><span data-ttu-id="1bdc8-170">WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1bdc8-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1bdc8-171">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-171">The default is OleTransactions.</span></span> <span data-ttu-id="1bdc8-172">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="1bdc8-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="1bdc8-173">transferMode</span></span>|<span data-ttu-id="1bdc8-174">A <xref:System.ServiceModel.TransferMode> iletileri olup ara belleğe veya akışa veya istek belirten değeri veya yanıt.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bdc8-175">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bdc8-175">Child Elements</span></span>  
  
|<span data-ttu-id="1bdc8-176">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bdc8-176">Element</span></span>|<span data-ttu-id="1bdc8-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bdc8-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bdc8-178">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="1bdc8-179">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="1bdc8-180">Bu öğe türünde <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="1bdc8-181">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-181">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="1bdc8-182">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1bdc8-183">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1bdc8-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bdc8-184">Parent Elements</span></span>  
  
|<span data-ttu-id="1bdc8-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bdc8-185">Element</span></span>|<span data-ttu-id="1bdc8-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bdc8-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bdc8-187">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1bdc8-188">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bdc8-189">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bdc8-189">Remarks</span></span>  
 <span data-ttu-id="1bdc8-190">`NetNamedPipeBinding` İleti teslimi ve ikili ileti kodlama için adlandırılmış kanallar taşıma güvenliği kullanan varsayılan olarak, bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="1bdc8-191">Bu bağlamanın bir uygun Windows Communication Foundation (WCF) sistem tarafından sağlanan makine üzerindeki iletişim için bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="1bdc8-192">Ayrıca, işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="1bdc8-193">İçin varsayılan yapılandırmayı `NetNamedPipeBinding` tarafından sağlanan yapılandırma benzer `NetTcpBinding`, ancak WCF uygulaması yalnızca makine üzerindeki kullanılmak üzere tasarlanmıştır ve sonuç olarak daha az gösterilen özellik yoktur çünkü daha basit değil.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="1bdc8-194">En dikkat çekici fark `securityMode` yalnızca teklifleri ayarı `None` ve `Transport` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="1bdc8-195">SOAP güvenlik desteği dahil edilen bir seçenek değil.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="1bdc8-196">Güvenlik davranıştır isteğe bağlı kullanılarak yapılandırılabilir `securityMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bdc8-197">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bdc8-197">Example</span></span>  
 <span data-ttu-id="1bdc8-198">Aşağıdaki örnek, aynı makine üzerinde işlem içi iletişimi sağlayan netNamedPipeBinding bağlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="1bdc8-199">Adlandırılmış Kanallar makinelerde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="1bdc8-200">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="1bdc8-201">Bağlama türü belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="1bdc8-202">NetNamedPipeBinding bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="1bdc8-203">Uç nokta ile ada göre bağlama yapılandırması başvurmalıdır bir `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="1bdc8-204">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <binding   
                 closeTimeout="00:01:00"  
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
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bdc8-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bdc8-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="1bdc8-206">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1bdc8-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="1bdc8-207">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1bdc8-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1bdc8-208">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1bdc8-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1bdc8-209">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="1bdc8-209">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
