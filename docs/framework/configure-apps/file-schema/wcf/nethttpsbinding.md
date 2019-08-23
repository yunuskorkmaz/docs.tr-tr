---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 7f4bde18876c5e65adf3da100f180b9b18892d98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933089"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="cb6c4-101">\<netHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="cb6c4-101">\<netHttpsBinding></span></span>
<span data-ttu-id="cb6c4-102">Bir Windows Communication Foundation (WCF) hizmetinin HTTPS üzerinden iletişim kurabilen uç noktaları yapılandırmak ve göstermek için kullanabileceği bir bağlamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="cb6c4-103">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır, aksi takdirde HTTPS kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="cb6c4-104">Kök öğe</span><span class="sxs-lookup"><span data-stu-id="cb6c4-104">Root Element</span></span>  
<span data-ttu-id="cb6c4-105">Next öğesi</span><span class="sxs-lookup"><span data-stu-id="cb6c4-105">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6c4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb6c4-106">Syntax</span></span>  
  
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
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="cb6c4-107">Tür</span><span class="sxs-lookup"><span data-stu-id="cb6c4-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb6c4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb6c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb6c4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb6c4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb6c4-110">Attributes</span></span>  
  
|<span data-ttu-id="cb6c4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb6c4-111">Attribute</span></span>|<span data-ttu-id="cb6c4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb6c4-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="cb6c4-113">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="cb6c4-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cb6c4-115">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="cb6c4-116">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="cb6c4-117">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="cb6c4-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="cb6c4-119">Bir Internet kaynağı, yerel bir adresi varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="cb6c4-120">Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir "http://webserver/" ve "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="cb6c4-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="cb6c4-121">Bu özniteliğin ayarlanması, BasicHttpBinding ile yapılandırılan uç noktaların yerel kaynaklara erişirken proxy sunucusunu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="cb6c4-122">Bu öznitelik ise `true`, yerel Internet kaynaklarına yönelik istekler proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="cb6c4-123">İstemcilerin, bu öznitelik olarak `true`ayarlandığında aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini isterseniz ana bilgisayar adını (localhost yerine) kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="cb6c4-124">Bu öznitelik `false`olduğunda, tüm Internet istekleri proxy sunucu aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="cb6c4-125">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="cb6c4-126">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cb6c4-127">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-127">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="cb6c4-128">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="cb6c4-129">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="cb6c4-130">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="cb6c4-131">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-131">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="cb6c4-132">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-132">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="cb6c4-133">Arabellek Yöneticisi, arabellek havuzu kullanarak arabellek kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-133">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="cb6c4-134">Arabellekleri, kanalın dışına geldiklerinde hizmete göre işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-134">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="cb6c4-135">Arabellek havuzunda ileti yükünü işlemek için yeterli bellek yoksa, arabellek yöneticisinin CLR yığınından ek bellek ayırması gerekir ve bu da çöp toplama yükünü artırır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-135">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="cb6c4-136">CLR atık yığınından kapsamlı ayırma, arabellek havuzu boyutunun çok küçük olduğunu ve bu öznitelik tarafından belirtilen sınırı artırarak performansın daha büyük bir ayırma ile iyileşebileceğinin göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-136">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="cb6c4-137">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-137">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="cb6c4-138">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-138">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="cb6c4-139">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-139">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="cb6c4-140">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-140">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="cb6c4-141">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="cb6c4-142">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-142">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="cb6c4-143">SOAP iletisini kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-143">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="cb6c4-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cb6c4-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cb6c4-145">Metinleri Bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="cb6c4-146">MTOM Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="cb6c4-147">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-147">The default is Text.</span></span> <span data-ttu-id="cb6c4-148">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="cb6c4-149">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="cb6c4-150">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="cb6c4-151">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-151">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="cb6c4-152">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-152">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="cb6c4-153">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cb6c4-154">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="cb6c4-155">Bağlamanın XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-155">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="cb6c4-156">Varsayılan değer "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="cb6c4-156">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="cb6c4-157">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-157">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="cb6c4-158">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="cb6c4-159">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cb6c4-160">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-160">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="cb6c4-161">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-161">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="cb6c4-162">, Olarak `true`ayarlandıysa, bu ayar olmalıdır. `null` `useSystemWebProxy`</span><span class="sxs-lookup"><span data-stu-id="cb6c4-162">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="cb6c4-163">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-163">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="cb6c4-164">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="cb6c4-165">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cb6c4-166">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-166">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="cb6c4-167">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="cb6c4-168">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="cb6c4-169">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-169">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="cb6c4-170">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="cb6c4-171">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cb6c4-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cb6c4-172">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="cb6c4-173">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="cb6c4-174">UTF8 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="cb6c4-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="cb6c4-175">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-175">The default is UTF8.</span></span> <span data-ttu-id="cb6c4-176">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="cb6c4-177">İletilerin arabelleğe <xref:System.ServiceModel.TransferMode> alınıp alınmayacağını veya bir istek ya da yanıt üzerinde akış yapılıp yapılmayacağını belirten geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-177">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="cb6c4-178">Varsa, sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-178">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="cb6c4-179">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-179">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="cb6c4-180">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb6c4-180">Child Elements</span></span>  
  
|<span data-ttu-id="cb6c4-181">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb6c4-181">Element</span></span>|<span data-ttu-id="cb6c4-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb6c4-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb6c4-183">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="cb6c4-183">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="cb6c4-184">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="cb6c4-185">Bu öğe türündedir <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-185">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="cb6c4-186">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cb6c4-186">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="cb6c4-187">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-187">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="cb6c4-188">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-188">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb6c4-189">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb6c4-189">Parent Elements</span></span>  
  
|<span data-ttu-id="cb6c4-190">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb6c4-190">Element</span></span>|<span data-ttu-id="cb6c4-191">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb6c4-191">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb6c4-192">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb6c4-192">\<bindings></span></span>](bindings.md)|<span data-ttu-id="cb6c4-193">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-193">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb6c4-194">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb6c4-194">Remarks</span></span>  
 <span data-ttu-id="cb6c4-195">NetHttpsBinding, ileti göndermek için taşıma olarak HTTPS kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-195">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="cb6c4-196">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-196">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="cb6c4-197">Bir istek-yanıt sözleşmesiyle birlikte kullanıldığında, NetHttpsBinding, ikili kodlayıcı ile bir BasicHttpsBinding gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-197">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="cb6c4-198">Güvenlik varsayılan olarak kapalıdır, ancak [ \<Security >](security-of-basichttpbinding.md) alt öğesinin mode özniteliği değerinden `None`farklı bir değere ayarlanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-198">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="cb6c4-199">Varsayılan olarak bir "metin" ileti kodlaması ve UTF-8 metin kodlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-199">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb6c4-200">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb6c4-200">Example</span></span>  
 <span data-ttu-id="cb6c4-201">Aşağıdaki örnek, HTTPS iletişimi ve ilk <xref:System.ServiceModel.NetHttpBinding> ve ikinci nesil Web Hizmetleri ile en fazla birlikte çalışabilirlik sağlayan öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-201">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="cb6c4-202">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-202">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="cb6c4-203">Bağlama türü, `binding` `<endpoint>` öğesinin özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-203">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="cb6c4-204">Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-204">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="cb6c4-205">Uç noktanın, hizmetin aşağıdaki yapılandırma kodunda gösterildiği gibi, `bindingConfiguration` `<endpoint>` öğesinin özniteliğini kullanarak bağlama yapılandırmasına adı ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-205">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="cb6c4-206">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb6c4-206">Example</span></span>  
 <span data-ttu-id="cb6c4-207">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-207">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="cb6c4-208">Önceki örnekteki işlevsellik, bindingConfiguration bitiş noktası adresinden ve bağlamadan adından kaldırılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-208">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
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
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="cb6c4-209">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-209">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6c4-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb6c4-210">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="cb6c4-211">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="cb6c4-211">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cb6c4-212">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cb6c4-212">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cb6c4-213">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb6c4-213">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cb6c4-214">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb6c4-214">\<binding></span></span>](../../../misc/binding.md)
