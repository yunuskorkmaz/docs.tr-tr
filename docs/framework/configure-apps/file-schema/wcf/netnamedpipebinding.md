---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b54fb3886fa7dc10d34220062c71e52a73b93dd8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738819"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="00a0f-101">netNamedPipeBinding > \<</span><span class="sxs-lookup"><span data-stu-id="00a0f-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="00a0f-102">Makine içi çapraz süreç iletişimi için güvenli, güvenilir ve iyileştirilmiş olan bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00a0f-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="00a0f-103">Varsayılan olarak, güvenlik için WS-ReliableMessaging ile bir çalışma zamanı iletişim yığını, aktarım güvenliği için taşıma güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması.</span><span class="sxs-lookup"><span data-stu-id="00a0f-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="00a0f-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="00a0f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00a0f-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="00a0f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="00a0f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="00a0f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="00a0f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="00a0f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a0f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00a0f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00a0f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a0f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00a0f-110">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="00a0f-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00a0f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00a0f-111">Attributes</span></span>  
  
|<span data-ttu-id="00a0f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00a0f-112">Attribute</span></span>|<span data-ttu-id="00a0f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a0f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00a0f-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="00a0f-114">closeTimeout</span></span>|<span data-ttu-id="00a0f-115">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="00a0f-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="00a0f-116">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00a0f-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="00a0f-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="00a0f-118">hostNameComparisonMode</span></span>|<span data-ttu-id="00a0f-119">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="00a0f-120">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="00a0f-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="00a0f-121">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="00a0f-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="00a0f-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="00a0f-122">maxBufferPoolSize</span></span>|<span data-ttu-id="00a0f-123">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00a0f-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="00a0f-124">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="00a0f-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="00a0f-125">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="00a0f-126">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="00a0f-127">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00a0f-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="00a0f-128">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="00a0f-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="00a0f-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="00a0f-129">maxBufferSize</span></span>|<span data-ttu-id="00a0f-130">İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00a0f-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="00a0f-131">Arabellek doluysa, arabelleğin tekrar boş olması bitinceye kadar aşırı veriler temeldeki yuvada kalır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="00a0f-132">Bu değer `maxReceivedMessageSize` öznitelikten küçük olamaz.</span><span class="sxs-lookup"><span data-stu-id="00a0f-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="00a0f-133">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-133">The default is 65536.</span></span> <span data-ttu-id="00a0f-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="00a0f-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="00a0f-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="00a0f-135">maxConnections</span></span>|<span data-ttu-id="00a0f-136">Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00a0f-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="00a0f-137">Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="00a0f-138">Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="00a0f-139">Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="00a0f-140">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="00a0f-140">The default is 10.</span></span>|  
|<span data-ttu-id="00a0f-141">Değerini</span><span class="sxs-lookup"><span data-stu-id="00a0f-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="00a0f-142">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="00a0f-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="00a0f-143">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="00a0f-144">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="00a0f-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="00a0f-145">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-145">The default is 65536.</span></span>|  
|<span data-ttu-id="00a0f-146">name</span><span class="sxs-lookup"><span data-stu-id="00a0f-146">name</span></span>|<span data-ttu-id="00a0f-147">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="00a0f-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="00a0f-148">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="00a0f-149">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="00a0f-150">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="00a0f-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="00a0f-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="00a0f-151">openTimeout</span></span>|<span data-ttu-id="00a0f-152">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="00a0f-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="00a0f-153">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00a0f-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="00a0f-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="00a0f-155">receiveTimeout</span></span>|<span data-ttu-id="00a0f-156">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="00a0f-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="00a0f-157">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00a0f-158">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="00a0f-159">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="00a0f-159">sendTimeout</span></span>|<span data-ttu-id="00a0f-160">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="00a0f-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="00a0f-161">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="00a0f-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="00a0f-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="00a0f-163">transactionFlow</span></span>|<span data-ttu-id="00a0f-164">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="00a0f-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="00a0f-165">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-165">The default is `false`.</span></span>|  
|<span data-ttu-id="00a0f-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="00a0f-166">transactionProtocol</span></span>|<span data-ttu-id="00a0f-167">Bu bağlama ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="00a0f-168">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="00a0f-168">Valid values are</span></span><br /><br /> <span data-ttu-id="00a0f-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="00a0f-169">-   OleTransactions</span></span><br /><span data-ttu-id="00a0f-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="00a0f-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="00a0f-171">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-171">The default is OleTransactions.</span></span> <span data-ttu-id="00a0f-172">Bu öznitelik <xref:System.ServiceModel.TransactionProtocol>türündedir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="00a0f-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="00a0f-173">transferMode</span></span>|<span data-ttu-id="00a0f-174">İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten <xref:System.ServiceModel.TransferMode> bir değer.</span><span class="sxs-lookup"><span data-stu-id="00a0f-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00a0f-175">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a0f-175">Child Elements</span></span>  
  
|<span data-ttu-id="00a0f-176">Öğe</span><span class="sxs-lookup"><span data-stu-id="00a0f-176">Element</span></span>|<span data-ttu-id="00a0f-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a0f-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00a0f-178">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="00a0f-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="00a0f-179">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00a0f-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="00a0f-180">Bu öğe <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="00a0f-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="00a0f-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="00a0f-182">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00a0f-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="00a0f-183">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00a0f-184">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00a0f-184">Parent Elements</span></span>  
  
|<span data-ttu-id="00a0f-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="00a0f-185">Element</span></span>|<span data-ttu-id="00a0f-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a0f-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00a0f-187">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="00a0f-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="00a0f-188">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00a0f-189">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00a0f-189">Remarks</span></span>  
 <span data-ttu-id="00a0f-190">`NetNamedPipeBinding`, aktarım güvenliği, ileti teslimi için adlandırılmış kanallar ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="00a0f-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="00a0f-191">Bu bağlama, makineye yönelik iletişim için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="00a0f-192">Ayrıca işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="00a0f-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="00a0f-193">`NetNamedPipeBinding` varsayılan yapılandırması, `NetTcpBinding`tarafından sunulan yapılandırmaya benzerdir, ancak WCF uygulamasının yalnızca şirket içi kullanım için olduğu ve bu nedenle daha az sunulan özellik olduğu için daha basittir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="00a0f-194">En önemli fark, `securityMode` ayarının yalnızca `None` ve `Transport` seçeneklerini sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="00a0f-195">SOAP güvenlik desteği, eklenen bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="00a0f-196">Güvenlik davranışı, isteğe bağlı `securityMode` özniteliği kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00a0f-197">Örnek</span><span class="sxs-lookup"><span data-stu-id="00a0f-197">Example</span></span>  
 <span data-ttu-id="00a0f-198">Aşağıdaki örnek, aynı makinede çapraz işlem iletişimi sağlayan netNamedPipeBinding bağlamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="00a0f-199">Adlandırılmış kanallar makineler arasında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="00a0f-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="00a0f-200">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="00a0f-201">Bağlama türü, `<endpoint>` öğesinin `binding` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="00a0f-202">NetNamedPipeBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="00a0f-203">Uç noktanın bağlama yapılandırmasına bir `bindingConfiguration` özniteliğiyle ad ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00a0f-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="00a0f-204">Bu örnekte, bağlama yapılandırması Binding1 olarak adlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00a0f-204">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00a0f-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00a0f-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="00a0f-206">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="00a0f-206">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="00a0f-207">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="00a0f-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00a0f-208">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="00a0f-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="00a0f-209">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="00a0f-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
