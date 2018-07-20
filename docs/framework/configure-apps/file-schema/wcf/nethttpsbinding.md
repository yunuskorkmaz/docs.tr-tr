---
title: '&lt;netHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: fb279321cccc325700ac18697d484da20c685c9d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751314"
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="7a241-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7a241-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="7a241-103">Windows Communication Foundation (WCF) hizmetini yapılandırmak ve HTTPS üzerinden iletişim kuramıyor uç noktalarını kullanıma sunmak için kullanabileceğiniz bir bağlama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a241-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="7a241-104">Çift yönlü sözleşme ile kullanıldığında, Web yuvalarını kullanılacak, aksi takdirde HTTPS kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a241-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="7a241-105">Kök öğesi</span><span class="sxs-lookup"><span data-stu-id="7a241-105">Root Element</span></span>  
<span data-ttu-id="7a241-106">Bir sonraki öğe</span><span class="sxs-lookup"><span data-stu-id="7a241-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a241-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a241-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
           openTimeout="TimeSpan"   
           proxyAddress="URI"  
           receiveTimeout="TimeSpan"  
           sendTimeout="TimeSpan"  
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="7a241-108">Tür</span><span class="sxs-lookup"><span data-stu-id="7a241-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a241-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a241-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7a241-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a241-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a241-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a241-111">Attributes</span></span>  
  
|<span data-ttu-id="7a241-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a241-112">Attribute</span></span>|<span data-ttu-id="7a241-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a241-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="7a241-114">İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7a241-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="7a241-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7a241-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7a241-116">Tanımlama bilgileri kullan ASMX Web Hizmetleri ile etkileşim kurarken, bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a241-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="7a241-117">Bu şekilde, sunucudan döndürülen tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalandığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a241-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="7a241-118">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7a241-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7a241-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7a241-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7a241-120">Yerel bir adres varsa, yerel bir Internet kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7a241-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="7a241-121">Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir " http://webserver/" ve " http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="7a241-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="7a241-122">Bu öznitelik ayarlama BasicHttpBinding ile yapılandırılmış uç noktaları yerel kaynaklara erişirken proxy sunucusu kullanıp kullanmayacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="7a241-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="7a241-123">Bu öznitelik değilse `true`, yerel Internet kaynakların isteklerine proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="7a241-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="7a241-124">Bu öznitelik ayarlandığında hizmetler için aynı makinede konuşurken bir proxy üzerinden gitmek için istemcilerin istiyorsanız konak adı (localhost yerine) kullanın `true`.</span><span class="sxs-lookup"><span data-stu-id="7a241-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="7a241-125">Bu öznitelik olduğunda `false`, proxy sunucu üzerinden yapılan tüm Internet istekleri.</span><span class="sxs-lookup"><span data-stu-id="7a241-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="7a241-126">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7a241-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7a241-127">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a241-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a241-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7a241-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="7a241-129">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a241-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7a241-130">Bu öznitelik türünde `HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a241-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7a241-131">Varsayılan değer `StrongWildcard`, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="7a241-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7a241-132">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7a241-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="7a241-133">Varsayılan değer 524288 (0x80000): bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a241-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="7a241-134">Arabellek Yöneticisi arabellek havuzu kullanarak arabellekleri kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="7a241-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="7a241-135">Kanal dışında geldiğinizde arabellekleri hizmeti tarafından iletilerini işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7a241-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="7a241-136">İleti yükü işlemek için arabellek havuzunda yeterli bellek yoksa, arabellek Yöneticisi atık toplama yükünü artırır CLR yığınından ek bellek ayırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a241-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="7a241-137">CLR çöp yığınına gelen kapsamlı ayırma arabellek havuzu boyutu çok küçük olduğunu ve bu özniteliği tarafından belirtilen sınırı artırarak performansı ile daha büyük bir ayırma geliştirilebilir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="7a241-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7a241-138">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirtir bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="7a241-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="7a241-139">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="7a241-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7a241-140">Bu bağlama ile yapılandırılan kanalda alınan bir ileti için üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7a241-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7a241-141">İleti alıcı için çok büyük ise gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="7a241-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="7a241-142">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a241-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7a241-143">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="7a241-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="7a241-144">SOAP iletisi kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a241-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="7a241-145">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7a241-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7a241-146">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a241-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="7a241-147">-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a241-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="7a241-148">Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="7a241-148">The default is Text.</span></span> <span data-ttu-id="7a241-149">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="7a241-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="7a241-150">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="7a241-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7a241-151">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a241-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7a241-152">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7a241-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7a241-153">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="7a241-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7a241-154">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7a241-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7a241-155">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a241-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="7a241-156">XML ad alanı bağlamanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a241-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="7a241-157">Varsayılan değer " http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="7a241-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="7a241-158">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7a241-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="7a241-159">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7a241-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7a241-160">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a241-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a241-161">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7a241-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="7a241-162">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="7a241-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="7a241-163">Varsa `useSystemWebProxy` ayarlanır `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="7a241-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="7a241-164">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7a241-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7a241-165">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7a241-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7a241-166">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a241-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a241-167">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="7a241-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7a241-168">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7a241-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7a241-169">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a241-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a241-170">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7a241-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7a241-171">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7a241-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7a241-172">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7a241-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7a241-173">-BigEndianUnicode: Unicode BigEndian kodlama.</span><span class="sxs-lookup"><span data-stu-id="7a241-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="7a241-174">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="7a241-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="7a241-175">-UTF8: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="7a241-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7a241-176">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7a241-176">The default is UTF8.</span></span> <span data-ttu-id="7a241-177">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7a241-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="7a241-178">Geçerli bir <xref:System.ServiceModel.TransferMode> iletilerin ara belleğe veya bir istek veya yanıt akışı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7a241-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="7a241-179">Otomatik yapılandırılan HTTP Proxy'si sisteminin kullanılması gerekip gerekmediğini, varsa belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7a241-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="7a241-180">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7a241-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="7a241-181">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a241-181">Child Elements</span></span>  
  
|<span data-ttu-id="7a241-182">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a241-182">Element</span></span>|<span data-ttu-id="7a241-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a241-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a241-184">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7a241-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="7a241-185">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a241-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="7a241-186">Bu öğe türünde <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7a241-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="7a241-187">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="7a241-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7a241-188">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a241-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7a241-189">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7a241-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a241-190">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a241-190">Parent Elements</span></span>  
  
|<span data-ttu-id="7a241-191">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a241-191">Element</span></span>|<span data-ttu-id="7a241-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a241-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a241-193">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7a241-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7a241-194">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7a241-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a241-195">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a241-195">Remarks</span></span>  
 <span data-ttu-id="7a241-196">NetHttpsBinding ileti göndermek için HTTPS taşıma olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a241-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="7a241-197">Çift yönlü sözleşme ile kullanıldığında, Web yuvalarını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7a241-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="7a241-198">NetHttpsBinding BasicHttpsBinding ikili kodlama ile gibi davranacak bir istek-yanıt Sözleşmesi ile kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="7a241-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="7a241-199">Güvenlik varsayılan olarak devre dışıdır, ancak mod özniteliği ayarıyla eklenebilir [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) alt öğesi dışında bir değere `None`.</span><span class="sxs-lookup"><span data-stu-id="7a241-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="7a241-200">Varsayılan kodlama "Metin" İleti kodlama ve UTF-8 metnini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a241-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a241-201">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a241-201">Example</span></span>  
 <span data-ttu-id="7a241-202">Aşağıdaki örnek kullanımını gösteren <xref:System.ServiceModel.NetHttpBinding> , HTTPS iletişimi ve maksimum birlikte çalışabilirliği ilk - ve second - generation ile Web hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a241-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="7a241-203">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7a241-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="7a241-204">Bağlama türü kullanılarak belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7a241-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="7a241-205">Temel bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7a241-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="7a241-206">Uç nokta bağlama yapılandırması adıyla kullanarak başvurmalıdır `bindingConfiguration` özniteliği `<endpoint>` hizmeti için aşağıdaki yapılandırma kodda gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="7a241-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard" 
               receiveTimeout="00:10:00" 
               sendTimeout="00:10:00" 
               openTimeout="00:10:00" 
               closeTimeout="00:10:00" 
               maxReceivedMessageSize="65536" 
               maxBufferSize="65536" 
               maxBufferPoolSize="524288" 
               transferMode="Buffered" 
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="7a241-207">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a241-207">Example</span></span>  
 <span data-ttu-id="7a241-208">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7a241-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7a241-209">Önceki örnekte işlevinden uç nokta adresi ve bağlama adı frm bindingConfiguration kaldırarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a241-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7a241-210">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a241-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a241-211">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a241-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="7a241-212">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7a241-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7a241-213">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7a241-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7a241-214">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="7a241-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7a241-215">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7a241-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
