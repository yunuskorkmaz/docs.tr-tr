---
title: '&lt;netHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 2dbcdbe7fff758bab0e932817feddab398ed9ed1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466562"
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="4ea5a-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4ea5a-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="4ea5a-103">Bir Windows Communication Foundation (WCF) hizmeti yapılandırmak ve HTTPS üzerinden iletişim kurabilen bitiş noktaları ortaya çıkarmak için kullanabileceğiniz bir bağlama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="4ea5a-104">Çift yönlü sözleşme ile kullanıldığında, Web yuvaları kullanılır, aksi takdirde HTTPS kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="4ea5a-105">Kök öğe</span><span class="sxs-lookup"><span data-stu-id="4ea5a-105">Root Element</span></span>  
<span data-ttu-id="4ea5a-106">Sonraki öğeye</span><span class="sxs-lookup"><span data-stu-id="4ea5a-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea5a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ea5a-107">Syntax</span></span>  

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
  
## <a name="type"></a><span data-ttu-id="4ea5a-108">Tür</span><span class="sxs-lookup"><span data-stu-id="4ea5a-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ea5a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4ea5a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ea5a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ea5a-111">Attributes</span></span>  
  
|<span data-ttu-id="4ea5a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ea5a-112">Attribute</span></span>|<span data-ttu-id="4ea5a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ea5a-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="4ea5a-114">İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="4ea5a-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4ea5a-116">Tanımlama bilgileri kullanan ASMX Web Hizmetleri ile etkileşim kurduğunuzda bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="4ea5a-117">Bu şekilde, sunucudan döndürülen tanımlama bilgilerini aydaki hizmet için tüm istemci isteklerini otomatik olarak kopyalanır emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="4ea5a-118">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="4ea5a-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4ea5a-120">Bir Internet kaynağına, yerel adres varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="4ea5a-121">Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir "http://webserver/" ve "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="4ea5a-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="4ea5a-122">Bu öznitelik ayarlama BasicHttpBinding ile yapılandırılmış uç noktaları yerel kaynaklara erişirken proxy sunucusu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="4ea5a-123">Bu öznitelik ise `true`, istekleri yerel Internet kaynakları için proxy sunucusu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="4ea5a-124">Bu öznitelik ayarlandığında Hizmetleri aynı makinede konuşurken bir proxy üzerinden Git istemcilerin istiyorsanız ana bilgisayarın adı (localhost yerine) kullanın `true`.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="4ea5a-125">Bu öznitelik olduğunda `false`, tüm Internet isteklerini Ara sunucu üzerinden yapılır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="4ea5a-126">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4ea5a-127">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ea5a-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="4ea5a-129">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4ea5a-130">Bu öznitelik türünde `HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4ea5a-131">Varsayılan değer `StrongWildcard`, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="4ea5a-132">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan maksimum belleğin belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="4ea5a-133">Varsayılan değer: 524288 (0x80000) bayt.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="4ea5a-134">Arabellek Yöneticisi bir arabellek havuzu kullanarak arabellekler maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="4ea5a-135">Bunlar dışında kanal geldiğinizde arabellekler iletilerini işlemek için hizmet tarafından gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="4ea5a-136">İleti yükü işlemek için arabellek havuzunda yeterli bellek yoksa, arabellek Yöneticisi çöp toplama taşması artıran CLR yığından ek bellek tahsis etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="4ea5a-137">CLR çöp yığınındaki gelen kapsamlı ayırma arabellek havuzu boyutu çok küçük olduğunu ve bu özniteliği tarafından belirtilen sınırı artırarak performans daha büyük bir ayırma ile geliştirilebilir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="4ea5a-138">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabellek, bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="4ea5a-139">65.536 bayt varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="4ea5a-140">Bu bağlama ile yapılandırılan bir kanalda alınan iletinin üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu tanımlar. pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4ea5a-141">İleti alıcısı için çok büyük ise, gönderici bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="4ea5a-142">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4ea5a-143">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="4ea5a-144">SOAP iletisi kodlamak için kullanılan Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="4ea5a-145">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4ea5a-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4ea5a-146">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="4ea5a-147">-Mtom: ileti aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="4ea5a-148">Metin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-148">The default is Text.</span></span> <span data-ttu-id="4ea5a-149">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="4ea5a-150">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4ea5a-151">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4ea5a-152">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4ea5a-153">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4ea5a-154">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4ea5a-155">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ea5a-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="4ea5a-156">XML ad alanı bağlamanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="4ea5a-157">Varsayılan değer " http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="4ea5a-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="4ea5a-158">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="4ea5a-159">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4ea5a-160">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ea5a-161">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="4ea5a-162">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="4ea5a-163">Varsa `useSystemWebProxy` ayarlanır `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="4ea5a-164">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4ea5a-165">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4ea5a-166">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ea5a-167">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4ea5a-168">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4ea5a-169">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ea5a-170">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="4ea5a-171">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4ea5a-172">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4ea5a-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4ea5a-173">-BigEndianUnicode: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="4ea5a-174">-Unicode: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="4ea5a-175">-UTF8: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="4ea5a-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4ea5a-176">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-176">The default is UTF8.</span></span> <span data-ttu-id="4ea5a-177">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="4ea5a-178">Geçerli bir <xref:System.ServiceModel.TransferMode> iletilerin ara belleğe veya bir istek veya yanıtı belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="4ea5a-179">Otomatik yapılandırılan HTTP Ara sunucusu sisteminin kullanılması gerekip gerekmediğini, varsa belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="4ea5a-180">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="4ea5a-181">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea5a-181">Child Elements</span></span>  
  
|<span data-ttu-id="4ea5a-182">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ea5a-182">Element</span></span>|<span data-ttu-id="4ea5a-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ea5a-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea5a-184">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4ea5a-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="4ea5a-185">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="4ea5a-186">Bu öğe türünde <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="4ea5a-187">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="4ea5a-187">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4ea5a-188">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4ea5a-189">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ea5a-190">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ea5a-190">Parent Elements</span></span>  
  
|<span data-ttu-id="4ea5a-191">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ea5a-191">Element</span></span>|<span data-ttu-id="4ea5a-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ea5a-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ea5a-193">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4ea5a-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="4ea5a-194">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ea5a-195">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ea5a-195">Remarks</span></span>  
 <span data-ttu-id="4ea5a-196">NetHttpsBinding, aktarım olarak ileti göndermek için HTTPS kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="4ea5a-197">Çift yönlü sözleşme ile kullanıldığında, Web yuvaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="4ea5a-198">NetHttpsBinding ikili Kodlayıcı ile bir BasicHttpsBinding gibi davranacak bir istek-yanıt Sözleşmesi ile kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="4ea5a-199">Güvenlik için varsayılan olarak devre dışıdır, ancak bu mod özniteliği ayarıyla eklenebilir [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) dışında bir değeri alt öğeye `None`.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="4ea5a-200">Bir "Metin" İleti kodlama ve UTF-8 metin kodlama varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ea5a-201">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea5a-201">Example</span></span>  
 <span data-ttu-id="4ea5a-202">Aşağıdaki örnek, kullanımını gösterir <xref:System.ServiceModel.NetHttpBinding> , HTTPS iletişimi ve en fazla birlikte çalışabilirlik ilk - ve second - generation ile Web hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="4ea5a-203">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4ea5a-204">Bağlama türü kullanarak belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="4ea5a-205">Temel bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="4ea5a-206">Uç nokta bağlama yapılandırması adıyla kullanarak başvurmalıdır `bindingConfiguration` özniteliği `<endpoint>` hizmeti için aşağıdaki yapılandırma kodda gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4ea5a-207">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ea5a-207">Example</span></span>  
 <span data-ttu-id="4ea5a-208">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4ea5a-209">Önceki örnekten gelen işlevi, uç nokta adresini ve bağlama adı frm bindingConfiguration kaldırma tarafından gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
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
  
 <span data-ttu-id="4ea5a-210">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ea5a-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea5a-211">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea5a-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="4ea5a-212">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4ea5a-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4ea5a-213">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4ea5a-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4ea5a-214">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="4ea5a-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="4ea5a-215">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4ea5a-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
