---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139472"
---
# \<netNamedPipeBinding>
<span data-ttu-id="0739c-101">Makine içi çapraz süreç iletişimi için güvenli, güvenilir ve iyileştirilmiş olan bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0739c-101">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="0739c-102">Varsayılan olarak, güvenlik için WS-ReliableMessaging ile bir çalışma zamanı iletişim yığını, aktarım güvenliği için taşıma güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması.</span><span class="sxs-lookup"><span data-stu-id="0739c-102">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="0739c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0739c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0739c-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0739c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0739c-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="0739c-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0739c-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0739c-106">Attributes</span></span>  
  
|<span data-ttu-id="0739c-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0739c-107">Attribute</span></span>|<span data-ttu-id="0739c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0739c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0739c-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0739c-109">closeTimeout</span></span>|<span data-ttu-id="0739c-110"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0739c-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0739c-111">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="0739c-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0739c-112">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0739c-113">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="0739c-113">hostNameComparisonMode</span></span>|<span data-ttu-id="0739c-114">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0739c-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0739c-115">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="0739c-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0739c-116">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="0739c-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="0739c-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0739c-117">maxBufferPoolSize</span></span>|<span data-ttu-id="0739c-118">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0739c-118">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0739c-119">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="0739c-119">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0739c-120">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="0739c-120">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0739c-121">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="0739c-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0739c-122">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0739c-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0739c-123">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="0739c-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="0739c-124">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="0739c-124">maxBufferSize</span></span>|<span data-ttu-id="0739c-125">İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0739c-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="0739c-126">Arabellek doluysa, arabelleğin tekrar boş olması bitinceye kadar aşırı veriler temeldeki yuvada kalır.</span><span class="sxs-lookup"><span data-stu-id="0739c-126">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="0739c-127">Bu değer öznitelikten küçük olamaz `maxReceivedMessageSize` .</span><span class="sxs-lookup"><span data-stu-id="0739c-127">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="0739c-128">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-128">The default is 65536.</span></span> <span data-ttu-id="0739c-129">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="0739c-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="0739c-130">maxConnections</span><span class="sxs-lookup"><span data-stu-id="0739c-130">maxConnections</span></span>|<span data-ttu-id="0739c-131">Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0739c-131">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="0739c-132">Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="0739c-132">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="0739c-133">Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="0739c-133">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="0739c-134">Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="0739c-134">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="0739c-135">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="0739c-135">The default is 10.</span></span>|  
|<span data-ttu-id="0739c-136">Değerini</span><span class="sxs-lookup"><span data-stu-id="0739c-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="0739c-137">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0739c-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0739c-138">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="0739c-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0739c-139">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0739c-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0739c-140">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-140">The default is 65536.</span></span>|  
|<span data-ttu-id="0739c-141">name</span><span class="sxs-lookup"><span data-stu-id="0739c-141">name</span></span>|<span data-ttu-id="0739c-142">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0739c-142">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0739c-143">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0739c-143">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0739c-144">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0739c-144">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0739c-145">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="0739c-145">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="0739c-146">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0739c-146">openTimeout</span></span>|<span data-ttu-id="0739c-147">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0739c-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0739c-148">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="0739c-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0739c-149">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-149">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0739c-150">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0739c-150">receiveTimeout</span></span>|<span data-ttu-id="0739c-151"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0739c-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0739c-152">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="0739c-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0739c-153">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-153">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="0739c-154">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="0739c-154">sendTimeout</span></span>|<span data-ttu-id="0739c-155"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0739c-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0739c-156">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="0739c-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0739c-157">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="0739c-158">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="0739c-158">transactionFlow</span></span>|<span data-ttu-id="0739c-159">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0739c-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="0739c-160">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="0739c-160">The default is `false`.</span></span>|  
|<span data-ttu-id="0739c-161">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="0739c-161">transactionProtocol</span></span>|<span data-ttu-id="0739c-162">Bu bağlama ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0739c-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="0739c-163">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="0739c-163">Valid values are</span></span><br /><br /> <span data-ttu-id="0739c-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="0739c-164">-   OleTransactions</span></span><br /><span data-ttu-id="0739c-165">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="0739c-165">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="0739c-166">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="0739c-166">The default is OleTransactions.</span></span> <span data-ttu-id="0739c-167">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="0739c-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="0739c-168">transferMode</span><span class="sxs-lookup"><span data-stu-id="0739c-168">transferMode</span></span>|<span data-ttu-id="0739c-169"><xref:System.ServiceModel.TransferMode>İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0739c-169">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0739c-170">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0739c-170">Child Elements</span></span>  
  
|<span data-ttu-id="0739c-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="0739c-171">Element</span></span>|<span data-ttu-id="0739c-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0739c-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="0739c-173">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0739c-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="0739c-174">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="0739c-174">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="0739c-175">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0739c-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0739c-176">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="0739c-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0739c-177">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0739c-177">Parent Elements</span></span>  
  
|<span data-ttu-id="0739c-178">Öğe</span><span class="sxs-lookup"><span data-stu-id="0739c-178">Element</span></span>|<span data-ttu-id="0739c-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0739c-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="0739c-180">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0739c-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0739c-181">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0739c-181">Remarks</span></span>  
 <span data-ttu-id="0739c-182">, `NetNamedPipeBinding` Aktarım güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0739c-182">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="0739c-183">Bu bağlama, makineye yönelik iletişim için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0739c-183">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="0739c-184">Ayrıca işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="0739c-184">It also supports transactions.</span></span>  
  
 <span data-ttu-id="0739c-185">İçin varsayılan yapılandırma, `NetNamedPipeBinding` tarafından sağlanmış olan yapılandırmaya benzerdir `NetTcpBinding` , ancak WCF uygulamasının yalnızca şirket içi kullanım için olduğu ve bu nedenle daha az sunulan özellik olduğu için daha basittir.</span><span class="sxs-lookup"><span data-stu-id="0739c-185">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="0739c-186">En önemli fark, `securityMode` ayarın yalnızca `None` ve seçeneklerini sunmanızdır `Transport` .</span><span class="sxs-lookup"><span data-stu-id="0739c-186">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="0739c-187">SOAP güvenlik desteği, eklenen bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="0739c-187">SOAP security support is not an included option.</span></span> <span data-ttu-id="0739c-188">Güvenlik davranışı, isteğe bağlı özniteliği kullanılarak yapılandırılabilir `securityMode` .</span><span class="sxs-lookup"><span data-stu-id="0739c-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0739c-189">Örnek</span><span class="sxs-lookup"><span data-stu-id="0739c-189">Example</span></span>  
 <span data-ttu-id="0739c-190">Aşağıdaki örnek, aynı makinede çapraz işlem iletişimi sağlayan netNamedPipeBinding bağlamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0739c-190">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="0739c-191">Adlandırılmış kanallar makineler arasında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0739c-191">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="0739c-192">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0739c-192">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0739c-193">Bağlama türü, `binding` öğesinin özniteliğinde belirtilir `<endpoint>` .</span><span class="sxs-lookup"><span data-stu-id="0739c-193">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="0739c-194">NetNamedPipeBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0739c-194">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="0739c-195">Uç nokta, bağlama yapılandırmasına ada göre bir özniteliği ile başvurmalıdır `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="0739c-195">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="0739c-196">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0739c-196">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0739c-197">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0739c-197">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="0739c-198">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0739c-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0739c-199">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0739c-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0739c-200">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0739c-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
