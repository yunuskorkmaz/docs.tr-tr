---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: a3d5b87bc53ca541776d9f131204868fbe25d5b1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738806"
---
# <a name="nettcpbinding"></a><span data-ttu-id="185c7-101">netTcpBinding > \<</span><span class="sxs-lookup"><span data-stu-id="185c7-101">\<netTcpBinding></span></span>

<span data-ttu-id="185c7-102">Makineler arası iletişim için güvenli, güvenilir ve iyileştirilmiş bir bağlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="185c7-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="185c7-103">Varsayılan olarak, ileti güvenliği ve kimlik doğrulaması, ileti teslimi için TCP ve ikili ileti kodlaması için Windows güvenliği ile bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="185c7-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="185c7-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="185c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="185c7-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="185c7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="185c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="185c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="185c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="185c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185c7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="185c7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="185c7-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="185c7-109">Attributes and elements</span></span>

<span data-ttu-id="185c7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="185c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="185c7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="185c7-111">Attributes</span></span>  
  
|<span data-ttu-id="185c7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="185c7-112">Attribute</span></span>|<span data-ttu-id="185c7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185c7-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="185c7-114">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="185c7-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="185c7-115">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="185c7-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="185c7-117">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="185c7-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="185c7-118">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="185c7-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="185c7-119">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="185c7-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="185c7-120">Dinleyicide kabul edilmesini bekleyen kanal sayısı üst sınırını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="185c7-120">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="185c7-121">Bu sınırın üzerinde olan bağlantılar, sınırın altındaki boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="185c7-121">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="185c7-122">`connectionTimeout` özniteliği, bir istemcinin bir bağlantı özel durumu oluşturmadan önce bağlanması için bekleyeceği süreyi sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="185c7-122">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="185c7-123">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="185c7-123">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="185c7-124">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="185c7-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="185c7-125">Varsayılan değer 512 \* 1024 bayttır.</span><span class="sxs-lookup"><span data-stu-id="185c7-125">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="185c7-126">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="185c7-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="185c7-127">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="185c7-128">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185c7-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="185c7-129">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="185c7-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="185c7-130">İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="185c7-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="185c7-131">`transferMode` özniteliği `Buffered`eşitse, bu öznitelik `maxReceivedMessageSize` öznitelik değerine eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-131">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="185c7-132">`transferMode` özniteliği `Streamed`eşitse, bu öznitelik `maxReceivedMessageSize` öznitelik değerinden daha fazla olamaz ve en azından üst bilgilerin boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-132">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="185c7-133">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-133">The default is 65536.</span></span> <span data-ttu-id="185c7-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="185c7-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="185c7-135">Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="185c7-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="185c7-136">Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="185c7-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="185c7-137">Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="185c7-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="185c7-138">Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="185c7-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="185c7-139">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="185c7-139">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="185c7-140">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="185c7-140">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="185c7-141">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="185c7-141">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="185c7-142">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="185c7-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="185c7-143">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-143">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="185c7-144">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="185c7-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="185c7-145">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="185c7-146">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="185c7-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="185c7-147">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="185c7-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="185c7-148">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="185c7-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="185c7-149">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="185c7-150">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-150">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="185c7-151">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="185c7-151">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="185c7-152">Bu `false`, her bağlama kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="185c7-152">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="185c7-153">İstemciler etkilenmediğinden, bu ayar yalnızca hizmetler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="185c7-153">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="185c7-154">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="185c7-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="185c7-155">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="185c7-156">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="185c7-157">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="185c7-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="185c7-158">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="185c7-159">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-159">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="185c7-160">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="185c7-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="185c7-161">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="185c7-161">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="185c7-162">Bu bağlama ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="185c7-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="185c7-163">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="185c7-163">Valid values are</span></span><br /><br /> <span data-ttu-id="185c7-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="185c7-164">-   OleTransactions</span></span><br /><span data-ttu-id="185c7-165">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="185c7-165">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="185c7-166">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="185c7-166">The default is OleTransactions.</span></span> <span data-ttu-id="185c7-167">Bu öznitelik <xref:System.ServiceModel.TransactionProtocol>türündedir.</span><span class="sxs-lookup"><span data-stu-id="185c7-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="185c7-168">İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten <xref:System.ServiceModel.TransferMode> bir değer.</span><span class="sxs-lookup"><span data-stu-id="185c7-168">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="185c7-169">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="185c7-169">Child elements</span></span>  
  
|<span data-ttu-id="185c7-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="185c7-170">Element</span></span>|<span data-ttu-id="185c7-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185c7-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="185c7-172">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="185c7-172">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="185c7-173">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="185c7-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="185c7-174">Bu öğe <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="185c7-174">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="185c7-175">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="185c7-175">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="185c7-176">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="185c7-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="185c7-177">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="185c7-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="185c7-178">[Reliableoturum > \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="185c7-178">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="185c7-179">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="185c7-179">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="185c7-180">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="185c7-180">Parent elements</span></span>  
  
|<span data-ttu-id="185c7-181">Öğe</span><span class="sxs-lookup"><span data-stu-id="185c7-181">Element</span></span>|<span data-ttu-id="185c7-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185c7-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="185c7-183">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="185c7-183">\<bindings></span></span>](bindings.md)|<span data-ttu-id="185c7-184">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="185c7-184">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185c7-185">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="185c7-185">Remarks</span></span>

<span data-ttu-id="185c7-186">Bu bağlama, aktarım güvenliği, ileti teslimi için TCP ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını üretir.</span><span class="sxs-lookup"><span data-stu-id="185c7-186">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="185c7-187">Bu bağlama, bir Intranet üzerinden iletişim kurmak için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.</span><span class="sxs-lookup"><span data-stu-id="185c7-187">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="185c7-188">`netTcpBinding` varsayılan yapılandırması, `wsHttpBinding`tarafından sunulan yapılandırmadan daha hızlıdır, ancak yalnızca WCF iletişimine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="185c7-188">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="185c7-189">Güvenlik davranışı, isteğe bağlı `securityMode` özniteliği kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="185c7-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="185c7-190">WS-ReliableMessaging kullanımı, isteğe bağlı `reliableSessionEnabled` özniteliği kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="185c7-190">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="185c7-191">Ancak güvenilir mesajlaşma varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="185c7-191">But reliable messaging is off by default.</span></span> <span data-ttu-id="185c7-192">Daha genel olarak, `wsHttpBinding` ve `basicHttpBinding` gibi HTTP sistem tarafından sunulan bağlamalar, varsayılan olarak açık hale getirmek üzere yapılandırılmıştır; ancak, örneğin, WS-\* ' n i n bir, destek almak için kabul etmeniz gerekir `netTcpBinding`. lerinize.</span><span class="sxs-lookup"><span data-stu-id="185c7-192">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="185c7-193">Bu, TCP varsayılan yapılandırmasının, HTTP bağlamaları için varsayılan olarak yapılandırılanlardan farklı uç noktalar arasında ileti alışverişi yaparken daha hızlı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="185c7-193">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="185c7-194">Örnek</span><span class="sxs-lookup"><span data-stu-id="185c7-194">Example</span></span>

<span data-ttu-id="185c7-195">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="185c7-195">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="185c7-196">Bağlama türü, `<endpoint>` öğesinin `binding` özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="185c7-196">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="185c7-197">NetTcpBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="185c7-197">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="185c7-198">Uç noktanın bağlama yapılandırmasına bir `bindingConfiguration` özniteliğiyle başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="185c7-198">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="185c7-199">Aşağıdaki örnekte, bir bağlama yapılandırması tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="185c7-199">In the following example, a binding configuration is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="185c7-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="185c7-200">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="185c7-201">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="185c7-201">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="185c7-202">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="185c7-202">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="185c7-203">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="185c7-203">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="185c7-204">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="185c7-204">\<binding></span></span>](bindings.md)
