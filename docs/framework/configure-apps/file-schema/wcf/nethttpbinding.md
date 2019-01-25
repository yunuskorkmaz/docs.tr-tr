---
title: '&lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: 97df2a9863bb4c1f31b24f0dbe370efaef0991a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715289"
---
# <a name="ltnethttpbindinggt"></a><span data-ttu-id="41bd9-102">&lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="41bd9-102">&lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="41bd9-103">Bir Windows Communication Foundation (WCF) hizmeti, yapılandırma ve HTTP üzerinden iletişim kurabilen bitiş noktaları ortaya çıkarmak için kullanabileceğiniz bir bağlama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41bd9-103">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="41bd9-104">Çift yönlü sözleşme ile kullanıldığında, Web yuvaları kullanılır, aksi takdirde HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
 <span data-ttu-id="41bd9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41bd9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="41bd9-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="41bd9-106">\<bindings></span></span>  
<span data-ttu-id="41bd9-107">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="41bd9-107">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bd9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41bd9-108">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="String"
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
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="41bd9-109">Tür</span><span class="sxs-lookup"><span data-stu-id="41bd9-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41bd9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41bd9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="41bd9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41bd9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41bd9-112">Attributes</span></span>  
  
|<span data-ttu-id="41bd9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41bd9-113">Attribute</span></span>|<span data-ttu-id="41bd9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41bd9-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="41bd9-115">İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd9-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="41bd9-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="41bd9-117">Tanımlama bilgileri kullanan ASMX Web Hizmetleri ile etkileşim kurduğunuzda bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41bd9-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="41bd9-118">Bu şekilde, sunucudan döndürülen tanımlama bilgilerini aydaki hizmet için tüm istemci isteklerini otomatik olarak kopyalanır emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41bd9-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="41bd9-119">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd9-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="41bd9-120">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="41bd9-121">Bir Internet kaynağına, yerel adres varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="41bd9-122">Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir "http://webserver/" ve "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="41bd9-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="41bd9-123">Bu öznitelik ayarlama BasicHttpBinding ile yapılandırılmış uç noktaları yerel kaynaklara erişirken proxy sunucusu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="41bd9-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="41bd9-124">Bu öznitelik ise `true`, istekleri yerel Internet kaynakları için proxy sunucusu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="41bd9-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="41bd9-125">Bu öznitelik ayarlandığında Hizmetleri aynı makinede konuşurken bir proxy üzerinden Git istemcilerin istiyorsanız ana bilgisayarın adı (localhost yerine) kullanın `true`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="41bd9-126">Bu öznitelik olduğunda `false`, tüm Internet isteklerini Ara sunucu üzerinden yapılır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="41bd9-127">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="41bd9-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="41bd9-128">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41bd9-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-129">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="41bd9-130">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="41bd9-131">Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-131">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="41bd9-132">Varsayılan değer `StrongWildcard`>, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-132">The default value is `StrongWildcard`>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="41bd9-133">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan maksimum belleğin belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd9-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="41bd9-134">Varsayılan değer: 524288 (0x80000) bayt.</span><span class="sxs-lookup"><span data-stu-id="41bd9-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="41bd9-135">Arabellek Yöneticisi bir arabellek havuzu kullanarak arabellekler maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="41bd9-136">Bunlar dışında kanal geldiğinizde arabellekler iletilerini işlemek için hizmet tarafından gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="41bd9-137">İleti yükü işlemek için arabellek havuzunda yeterli bellek yoksa, arabellek Yöneticisi çöp toplama taşması artıran CLR yığından ek bellek tahsis etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="41bd9-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="41bd9-138">CLR çöp yığınındaki gelen kapsamlı ayırma arabellek havuzu boyutu çok küçük olduğunu ve bu özniteliği tarafından belirtilen sınırı artırarak performans daha büyük bir ayırma ile geliştirilebilir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="41bd9-139">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabellek, bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd9-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="41bd9-140">65.536 bayt varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="41bd9-141">Bu bağlama ile yapılandırılan bir kanalda alınan iletinin üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu tanımlar. pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="41bd9-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="41bd9-142">İleti alıcısı için çok büyük ise, gönderici bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="41bd9-143">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41bd9-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="41bd9-144">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="41bd9-145">SOAP iletisi kodlamak için kullanılan Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="41bd9-146">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="41bd9-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41bd9-147">-Metni: Bir metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="41bd9-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="41bd9-148">-Mtom: İleti Aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="41bd9-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="41bd9-149">Metin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-149">The default is Text.</span></span> <span data-ttu-id="41bd9-150">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="41bd9-151">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="41bd9-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="41bd9-152">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="41bd9-153">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="41bd9-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="41bd9-154">Ayrıca, bu ad aynı türdeki bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="41bd9-155">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="41bd9-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="41bd9-156">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="41bd9-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="41bd9-157">XML ad alanı bağlamanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="41bd9-158">Varsayılan değer "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="41bd9-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="41bd9-159">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz özniteliği hizmetinin meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="41bd9-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="41bd9-160">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="41bd9-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="41bd9-161">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41bd9-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="41bd9-163">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="41bd9-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="41bd9-164">Varsa `useSystemWebProxy` ayarlanır `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="41bd9-165">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="41bd9-166">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="41bd9-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="41bd9-167">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41bd9-168">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="41bd9-169">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="41bd9-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="41bd9-170">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41bd9-171">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="41bd9-172">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="41bd9-173">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="41bd9-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41bd9-174">-   BigEndianUnicode: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="41bd9-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="41bd9-175">-Unicode: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="41bd9-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="41bd9-176">-   UTF8: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="41bd9-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="41bd9-177">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-177">The default is UTF8.</span></span> <span data-ttu-id="41bd9-178">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="41bd9-179">Geçerli bir <xref:System.ServiceModel.TransferMode> iletilerin ara belleğe veya bir istek veya yanıtı belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="41bd9-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="41bd9-180">Otomatik yapılandırılan HTTP Ara sunucusu sisteminin kullanılması gerekip gerekmediğini, varsa belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="41bd9-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="41bd9-181">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-181">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="41bd9-182">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41bd9-182">Child Elements</span></span>  
  
|<span data-ttu-id="41bd9-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="41bd9-183">Element</span></span>|<span data-ttu-id="41bd9-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41bd9-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41bd9-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="41bd9-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="41bd9-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="41bd9-187">Bu öğe türünde `NetHttpSecurityElement`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-187">This element is of type `NetHttpSecurityElement`.</span></span>|  
|[<span data-ttu-id="41bd9-188">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="41bd9-188">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="41bd9-189">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="41bd9-190">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="41bd9-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41bd9-191">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41bd9-191">Parent Elements</span></span>  
  
|<span data-ttu-id="41bd9-192">Öğe</span><span class="sxs-lookup"><span data-stu-id="41bd9-192">Element</span></span>|<span data-ttu-id="41bd9-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41bd9-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41bd9-194">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="41bd9-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="41bd9-195">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41bd9-196">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41bd9-196">Remarks</span></span>  
 <span data-ttu-id="41bd9-197">NetHttpBinding, aktarım olarak ileti göndermek için HTTP kullanır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-197">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="41bd9-198">Çift yönlü sözleşme ile kullanıldığında, Web yuvaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-198">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="41bd9-199">NetHttpBinding ikili Kodlayıcı ile bir BasicHttpBinding gibi davranacak bir istek-yanıt Sözleşmesi ile kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="41bd9-199">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="41bd9-200">Güvenlik için varsayılan olarak devre dışıdır, ancak bu mod özniteliği ayarıyla eklenebilir [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) dışında bir değeri alt öğeye `None`.</span><span class="sxs-lookup"><span data-stu-id="41bd9-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="41bd9-201">Bir "Metin" İleti kodlama ve UTF-8 metin kodlama varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="41bd9-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41bd9-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="41bd9-202">Example</span></span>  
 <span data-ttu-id="41bd9-203">Aşağıdaki örnek, kullanımını gösterir <xref:System.ServiceModel.NetHttpBinding> , HTTP iletişimi ve en fazla birlikte çalışabilirlik ilk - ve second - generation ile Web hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="41bd9-203">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="41bd9-204">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="41bd9-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="41bd9-205">Bağlama türü kullanarak belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="41bd9-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="41bd9-206">Temel bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırmasını tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="41bd9-207">Uç nokta bağlama yapılandırması adıyla kullanarak başvurmalıdır `bindingConfiguration` özniteliği `<endpoint>` hizmeti için aşağıdaki yapılandırma kodda gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="41bd9-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="41bd9-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="41bd9-208">Example</span></span>  
 <span data-ttu-id="41bd9-209">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="41bd9-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="41bd9-210">Önceki örnekte işlevselliği, uç nokta adresini ve bağlama adından bindingConfiguration kaldırarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="41bd9-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="41bd9-211">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="41bd9-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bd9-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41bd9-212">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="41bd9-213">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="41bd9-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="41bd9-214">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="41bd9-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="41bd9-215">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="41bd9-215">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="41bd9-216">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="41bd9-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
