---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 4e15a52603df12ea3e1332efcf707f7d0c389976
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430252"
---
# <a name="nethttpsbinding"></a><span data-ttu-id="3bf25-101">\<netHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="3bf25-101">\<netHttpsBinding></span></span>
<span data-ttu-id="3bf25-102">Bir Windows Communication Foundation (WCF) hizmetinin HTTPS üzerinden iletişim kurabilen uç noktaları yapılandırmak ve göstermek için kullanabileceği bir bağlamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bf25-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="3bf25-103">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır, aksi takdirde HTTPS kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
<span data-ttu-id="3bf25-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bf25-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3bf25-105">[**System. serviceModel >\<** ](system-servicemodel.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="3bf25-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3bf25-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3bf25-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3bf25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="3bf25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3bf25-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bf25-108">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="3bf25-109">Type</span><span class="sxs-lookup"><span data-stu-id="3bf25-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bf25-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf25-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3bf25-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bf25-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3bf25-112">Attributes</span></span>  
  
|<span data-ttu-id="3bf25-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3bf25-113">Attribute</span></span>|<span data-ttu-id="3bf25-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf25-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="3bf25-115">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="3bf25-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3bf25-117">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf25-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="3bf25-118">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf25-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="3bf25-119">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="3bf25-120">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3bf25-121">Bir Internet kaynağı, yerel bir adresi varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="3bf25-122">Yerel bir adres, aynı bilgisayarda, yerel LAN veya intranette bulunan ve sözdizimi, sözdizimi, "http://webserver/" ve "http://localhost/" URI 'Lerinde olduğu gibi bir nokta (.) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="3bf25-123">Bu özniteliğin ayarlanması, BasicHttpBinding ile yapılandırılan uç noktaların yerel kaynaklara erişirken proxy sunucusunu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3bf25-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="3bf25-124">Bu öznitelik `true`, yerel Internet kaynaklarına yönelik istekler proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="3bf25-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="3bf25-125">İstemcilerin, bu öznitelik `true`olarak ayarlandığında aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini isterseniz ana bilgisayar adını (localhost yerine) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bf25-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="3bf25-126">Bu öznitelik `false`olduğunda, tüm Internet istekleri proxy sunucu aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="3bf25-127">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3bf25-128">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3bf25-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="3bf25-130">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="3bf25-131">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="3bf25-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="3bf25-132">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="3bf25-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="3bf25-133">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="3bf25-134">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="3bf25-135">Arabellek Yöneticisi, arabellek havuzu kullanarak arabellek kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="3bf25-136">Arabellekleri, kanalın dışına geldiklerinde hizmete göre işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="3bf25-137">Arabellek havuzunda ileti yükünü işlemek için yeterli bellek yoksa, arabellek yöneticisinin CLR yığınından ek bellek ayırması gerekir ve bu da çöp toplama yükünü artırır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="3bf25-138">CLR atık yığınından kapsamlı ayırma, arabellek havuzu boyutunun çok küçük olduğunu ve bu öznitelik tarafından belirtilen sınırı artırarak performansın daha büyük bir ayırma ile iyileşebileceğinin göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="3bf25-139">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="3bf25-140">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="3bf25-141">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3bf25-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="3bf25-142">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="3bf25-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="3bf25-143">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bf25-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="3bf25-144">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="3bf25-145">SOAP iletisini kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3bf25-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="3bf25-146">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3bf25-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3bf25-147">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bf25-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="3bf25-148">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bf25-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="3bf25-149">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-149">The default is Text.</span></span> <span data-ttu-id="3bf25-150">Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="3bf25-151">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3bf25-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3bf25-152">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3bf25-153">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-153">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3bf25-154">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3bf25-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="3bf25-155">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3bf25-156">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3bf25-157">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-157">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="3bf25-158">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="3bf25-158">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="3bf25-159">`useSystemWebProxy` `true`olarak ayarlanırsa, bu ayar `null`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-159">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="3bf25-160">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-160">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3bf25-161">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3bf25-162">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3bf25-163">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-163">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3bf25-164">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3bf25-165">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3bf25-166">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-166">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="3bf25-167">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3bf25-167">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3bf25-168">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3bf25-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3bf25-169">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="3bf25-169">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="3bf25-170">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="3bf25-170">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="3bf25-171">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="3bf25-171">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3bf25-172">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-172">The default is UTF8.</span></span> <span data-ttu-id="3bf25-173">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="3bf25-174">İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt üzerinde akış yapılıp yapılmayacağını belirten geçerli bir <xref:System.ServiceModel.TransferMode> değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-174">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="3bf25-175">Varsa, sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3bf25-175">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="3bf25-176">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-176">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="3bf25-177">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf25-177">Child Elements</span></span>  
  
|<span data-ttu-id="3bf25-178">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bf25-178">Element</span></span>|<span data-ttu-id="3bf25-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf25-179">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bf25-180">\<güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3bf25-180">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="3bf25-181">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3bf25-181">Defines the security settings for the binding.</span></span> <span data-ttu-id="3bf25-182">Bu öğe <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-182">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|<span data-ttu-id="3bf25-183">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3bf25-183">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="3bf25-184">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3bf25-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3bf25-185">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3bf25-186">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bf25-186">Parent Elements</span></span>  
  
|<span data-ttu-id="3bf25-187">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bf25-187">Element</span></span>|<span data-ttu-id="3bf25-188">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bf25-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bf25-189">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3bf25-189">\<bindings></span></span>](bindings.md)|<span data-ttu-id="3bf25-190">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf25-191">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bf25-191">Remarks</span></span>  
 <span data-ttu-id="3bf25-192">NetHttpsBinding, ileti göndermek için taşıma olarak HTTPS kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-192">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="3bf25-193">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-193">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="3bf25-194">Bir istek-yanıt sözleşmesiyle birlikte kullanıldığında, NetHttpsBinding, ikili kodlayıcı ile bir BasicHttpsBinding gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-194">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="3bf25-195">Güvenlik varsayılan olarak kapalıdır, ancak [\<security >](security-of-basichttpbinding.md) alt öğesinin mode özniteliği `None`dışında bir değere ayarlanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-195">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="3bf25-196">Varsayılan olarak bir "metin" ileti kodlaması ve UTF-8 metin kodlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bf25-196">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bf25-197">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bf25-197">Example</span></span>  
 <span data-ttu-id="3bf25-198">Aşağıdaki örnek, ilk ve ikinci nesil Web hizmetleriyle HTTPS iletişimi ve en fazla birlikte çalışabilirlik sağlayan <xref:System.ServiceModel.NetHttpBinding> kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-198">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="3bf25-199">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3bf25-200">Bağlama türü, `<endpoint>` öğesinin `binding` özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-200">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="3bf25-201">Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-201">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="3bf25-202">Uç noktanın, hizmet için aşağıdaki yapılandırma kodunda gösterildiği gibi `<endpoint>` öğesinin `bindingConfiguration` özniteliğini kullanarak, bağlama yapılandırmasına ad ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-202">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3bf25-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bf25-203">Example</span></span>  
 <span data-ttu-id="3bf25-204">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-204">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3bf25-205">Önceki örnekteki işlevsellik, bindingConfiguration bitiş noktası adresinden ve bağlamadan adından kaldırılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3bf25-205">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="3bf25-206">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3bf25-206">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf25-207">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf25-207">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="3bf25-208">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3bf25-208">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3bf25-209">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3bf25-209">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3bf25-210">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3bf25-210">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3bf25-211">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="3bf25-211">\<binding></span></span>](bindings.md)
