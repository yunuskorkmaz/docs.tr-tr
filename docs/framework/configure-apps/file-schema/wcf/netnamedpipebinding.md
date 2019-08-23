---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 475c7dfa618cffa70942fc1e02a75910da847701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933103"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="956d4-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="956d4-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="956d4-102">Makine içi çapraz süreç iletişimi için güvenli, güvenilir ve iyileştirilmiş olan bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="956d4-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="956d4-103">Varsayılan olarak, güvenlik için WS-ReliableMessaging ile bir çalışma zamanı iletişim yığını, aktarım güvenliği için taşıma güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması.</span><span class="sxs-lookup"><span data-stu-id="956d4-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="956d4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="956d4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="956d4-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="956d4-105">\<bindings></span></span>  
<span data-ttu-id="956d4-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="956d4-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="956d4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="956d4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="956d4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="956d4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="956d4-109">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="956d4-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="956d4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="956d4-110">Attributes</span></span>  
  
|<span data-ttu-id="956d4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="956d4-111">Attribute</span></span>|<span data-ttu-id="956d4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="956d4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="956d4-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="956d4-113">closeTimeout</span></span>|<span data-ttu-id="956d4-114">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="956d4-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="956d4-115">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="956d4-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="956d4-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="956d4-117">hostNameComparisonMode</span></span>|<span data-ttu-id="956d4-118">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="956d4-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="956d4-119">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="956d4-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="956d4-120">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="956d4-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="956d4-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="956d4-121">maxBufferPoolSize</span></span>|<span data-ttu-id="956d4-122">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="956d4-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="956d4-123">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="956d4-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="956d4-124">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="956d4-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="956d4-125">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="956d4-126">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="956d4-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="956d4-127">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="956d4-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="956d4-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="956d4-128">maxBufferSize</span></span>|<span data-ttu-id="956d4-129">İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="956d4-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="956d4-130">Arabellek doluysa, arabelleğin tekrar boş olması bitinceye kadar aşırı veriler temeldeki yuvada kalır.</span><span class="sxs-lookup"><span data-stu-id="956d4-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="956d4-131">Bu değer öznitelikten `maxReceivedMessageSize` küçük olamaz.</span><span class="sxs-lookup"><span data-stu-id="956d4-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="956d4-132">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-132">The default is 65536.</span></span> <span data-ttu-id="956d4-133">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="956d4-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="956d4-134">maxConnections</span><span class="sxs-lookup"><span data-stu-id="956d4-134">maxConnections</span></span>|<span data-ttu-id="956d4-135">Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="956d4-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="956d4-136">Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="956d4-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="956d4-137">Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="956d4-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="956d4-138">Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="956d4-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="956d4-139">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="956d4-139">The default is 10.</span></span>|  
|<span data-ttu-id="956d4-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="956d4-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="956d4-141">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="956d4-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="956d4-142">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="956d4-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="956d4-143">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="956d4-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="956d4-144">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-144">The default is 65536.</span></span>|  
|<span data-ttu-id="956d4-145">name</span><span class="sxs-lookup"><span data-stu-id="956d4-145">name</span></span>|<span data-ttu-id="956d4-146">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="956d4-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="956d4-147">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="956d4-148">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="956d4-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="956d4-149">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="956d4-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="956d4-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="956d4-150">openTimeout</span></span>|<span data-ttu-id="956d4-151">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="956d4-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="956d4-152">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="956d4-153">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="956d4-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="956d4-154">receiveTimeout</span></span>|<span data-ttu-id="956d4-155">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="956d4-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="956d4-156">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="956d4-157">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="956d4-158">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="956d4-158">sendTimeout</span></span>|<span data-ttu-id="956d4-159">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="956d4-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="956d4-160">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="956d4-161">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="956d4-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="956d4-162">transactionFlow</span></span>|<span data-ttu-id="956d4-163">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="956d4-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="956d4-164">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="956d4-164">The default is `false`.</span></span>|  
|<span data-ttu-id="956d4-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="956d4-165">transactionProtocol</span></span>|<span data-ttu-id="956d4-166">Bu bağlama ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="956d4-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="956d4-167">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="956d4-167">Valid values are</span></span><br /><br /> <span data-ttu-id="956d4-168">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="956d4-168">-   OleTransactions</span></span><br /><span data-ttu-id="956d4-169">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="956d4-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="956d4-170">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="956d4-170">The default is OleTransactions.</span></span> <span data-ttu-id="956d4-171">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="956d4-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="956d4-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="956d4-172">transferMode</span></span>|<span data-ttu-id="956d4-173">İletilerin <xref:System.ServiceModel.TransferMode> arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="956d4-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="956d4-174">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="956d4-174">Child Elements</span></span>  
  
|<span data-ttu-id="956d4-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="956d4-175">Element</span></span>|<span data-ttu-id="956d4-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="956d4-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="956d4-177">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="956d4-177">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="956d4-178">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="956d4-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="956d4-179">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="956d4-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="956d4-180">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="956d4-180">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="956d4-181">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="956d4-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="956d4-182">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="956d4-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="956d4-183">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="956d4-183">Parent Elements</span></span>  
  
|<span data-ttu-id="956d4-184">Öğe</span><span class="sxs-lookup"><span data-stu-id="956d4-184">Element</span></span>|<span data-ttu-id="956d4-185">Açıklama</span><span class="sxs-lookup"><span data-stu-id="956d4-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="956d4-186">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="956d4-186">\<bindings></span></span>](bindings.md)|<span data-ttu-id="956d4-187">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="956d4-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="956d4-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="956d4-188">Remarks</span></span>  
 <span data-ttu-id="956d4-189">, `NetNamedPipeBinding` Aktarım güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="956d4-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="956d4-190">Bu bağlama, makineye yönelik iletişim için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.</span><span class="sxs-lookup"><span data-stu-id="956d4-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="956d4-191">Ayrıca işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="956d4-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="956d4-192">İçin `NetNamedPipeBinding` varsayılan yapılandırma, `NetTcpBinding`tarafından sağlanmış olan yapılandırmaya benzerdir, ancak WCF uygulamasının yalnızca şirket içi kullanım için olduğu ve bu nedenle daha az sunulan özellik olduğu için daha basittir.</span><span class="sxs-lookup"><span data-stu-id="956d4-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="956d4-193">En önemli fark `securityMode` , ayarın yalnızca `None` ve `Transport` seçeneklerini sunmanızdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="956d4-194">SOAP güvenlik desteği, eklenen bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="956d4-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="956d4-195">Güvenlik davranışı, isteğe bağlı `securityMode` özniteliği kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="956d4-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="956d4-196">Örnek</span><span class="sxs-lookup"><span data-stu-id="956d4-196">Example</span></span>  
 <span data-ttu-id="956d4-197">Aşağıdaki örnek, aynı makinede çapraz işlem iletişimi sağlayan netNamedPipeBinding bağlamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="956d4-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="956d4-198">Adlandırılmış kanallar makineler arasında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="956d4-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="956d4-199">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="956d4-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="956d4-200">Bağlama türü, `binding` `<endpoint>` öğesinin özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="956d4-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="956d4-201">NetNamedPipeBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="956d4-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="956d4-202">Uç nokta, bağlama yapılandırmasına ada göre bir `bindingConfiguration` özniteliği ile başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="956d4-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="956d4-203">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="956d4-203">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="956d4-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="956d4-204">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="956d4-205">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="956d4-205">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="956d4-206">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="956d4-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="956d4-207">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="956d4-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="956d4-208">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="956d4-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
