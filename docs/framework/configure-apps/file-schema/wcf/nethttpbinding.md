---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: fce40f4cea856a52229a4586d216670ff61c2423
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397680"
---
# <a name="nethttpbinding"></a><span data-ttu-id="f0d85-101">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f0d85-101">\<netHttpBinding></span></span>
<span data-ttu-id="f0d85-102">Bir Windows Communication Foundation (WCF) hizmetinin HTTP üzerinden iletişim kurabilen uç noktaları yapılandırmak ve göstermek için kullanabileceği bir bağlamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0d85-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTP.</span></span> <span data-ttu-id="f0d85-103">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web yuvaları kullanılır, aksi takdirde HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-103">When used with a duplex contract, Web Sockets will be used, otherwise HTTP will be used.</span></span>  
  
<span data-ttu-id="f0d85-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0d85-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0d85-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f0d85-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f0d85-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f0d85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f0d85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="f0d85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d85-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0d85-108">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f0d85-109">Tür</span><span class="sxs-lookup"><span data-stu-id="f0d85-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0d85-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0d85-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0d85-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0d85-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0d85-112">Attributes</span></span>  
  
|<span data-ttu-id="f0d85-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0d85-113">Attribute</span></span>|<span data-ttu-id="f0d85-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0d85-114">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="f0d85-115">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d85-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="f0d85-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f0d85-117">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0d85-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="f0d85-118">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0d85-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="f0d85-119">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d85-119">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="f0d85-120">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-120">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f0d85-121">Bir Internet kaynağı, yerel bir adresi varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-121">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="f0d85-122">Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir "http://webserver/" ve "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="f0d85-122">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="f0d85-123">Bu özniteliğin ayarlanması, BasicHttpBinding ile yapılandırılan uç noktaların yerel kaynaklara erişirken proxy sunucusunu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f0d85-123">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="f0d85-124">Bu öznitelik ise `true`, yerel Internet kaynaklarına yönelik istekler proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f0d85-124">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="f0d85-125">İstemcilerin, bu öznitelik olarak `true`ayarlandığında aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini isterseniz ana bilgisayar adını (localhost yerine) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d85-125">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="f0d85-126">Bu öznitelik `false`olduğunda, tüm Internet istekleri proxy sunucu aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-126">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="f0d85-127">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f0d85-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f0d85-128">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f0d85-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-129">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="f0d85-130">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f0d85-131">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="f0d85-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f0d85-132">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="f0d85-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f0d85-133">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d85-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="f0d85-134">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="f0d85-135">Arabellek Yöneticisi, arabellek havuzu kullanarak arabellek kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="f0d85-136">Arabellekleri, kanalın dışına geldiklerinde hizmete göre işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="f0d85-137">Arabellek havuzunda ileti yükünü işlemek için yeterli bellek yoksa, arabellek yöneticisinin CLR yığınından ek bellek ayırması gerekir ve bu da çöp toplama yükünü artırır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="f0d85-138">CLR atık yığınından kapsamlı ayırma, arabellek havuzu boyutunun çok küçük olduğunu ve bu öznitelik tarafından belirtilen sınırı artırarak performansın daha büyük bir ayırma ile iyileşebileceğinin göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="f0d85-139">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d85-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="f0d85-140">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f0d85-141">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f0d85-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f0d85-142">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="f0d85-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="f0d85-143">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0d85-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f0d85-144">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="f0d85-145">SOAP iletisini kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0d85-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="f0d85-146">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f0d85-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0d85-147">Metinleri Bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d85-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="f0d85-148">MTOM Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0d85-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="f0d85-149">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-149">The default is Text.</span></span> <span data-ttu-id="f0d85-150">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="f0d85-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="f0d85-151">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f0d85-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f0d85-152">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f0d85-153">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f0d85-154">Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f0d85-155">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f0d85-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f0d85-156">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="f0d85-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="f0d85-157">Bağlamanın XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="f0d85-158">Varsayılan değer "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="f0d85-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="f0d85-159">Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="f0d85-160">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f0d85-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f0d85-161">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f0d85-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="f0d85-163">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="f0d85-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="f0d85-164">, Olarak `true`ayarlandıysa, bu ayar olmalıdır. `null` `useSystemWebProxy`</span><span class="sxs-lookup"><span data-stu-id="f0d85-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="f0d85-165">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f0d85-166">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f0d85-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f0d85-167">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f0d85-168">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f0d85-169">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f0d85-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f0d85-170">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f0d85-171">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="f0d85-172">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0d85-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f0d85-173">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f0d85-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0d85-174">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="f0d85-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="f0d85-175">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="f0d85-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f0d85-176">UTF8 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="f0d85-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f0d85-177">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-177">The default is UTF8.</span></span> <span data-ttu-id="f0d85-178">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f0d85-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="f0d85-179">İletilerin arabelleğe <xref:System.ServiceModel.TransferMode> alınıp alınmayacağını veya bir istek ya da yanıt üzerinde akış yapılıp yapılmayacağını belirten geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="f0d85-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="f0d85-180">Varsa, sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d85-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="f0d85-181">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-181">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="f0d85-182">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0d85-182">Child Elements</span></span>  
  
|<span data-ttu-id="f0d85-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0d85-183">Element</span></span>|<span data-ttu-id="f0d85-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0d85-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0d85-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f0d85-185">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="f0d85-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0d85-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="f0d85-187">Bu öğe türündedir <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f0d85-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="f0d85-188">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0d85-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="f0d85-189">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0d85-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f0d85-190">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f0d85-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0d85-191">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0d85-191">Parent Elements</span></span>  
  
|<span data-ttu-id="f0d85-192">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0d85-192">Element</span></span>|<span data-ttu-id="f0d85-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0d85-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0d85-194">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f0d85-194">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f0d85-195">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d85-196">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0d85-196">Remarks</span></span>  
 <span data-ttu-id="f0d85-197">NetHttpBinding ileti göndermek için taşıma olarak HTTP kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-197">The NetHttpBinding uses HTTP as the transport for sending messages.</span></span> <span data-ttu-id="f0d85-198">Bir çift yönlü sözleşmeyle birlikte kullanıldığında, Web Yuvaları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-198">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="f0d85-199">Bir istek ile kullanıldığında, yanıt sözleşmesi NetHttpBinding bir ikili kodlayıcı ile bir BasicHttpBinding gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-199">When used with a request-reply contract NetHttpBinding will behave like a BasicHttpBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="f0d85-200">Güvenlik varsayılan olarak kapalıdır, ancak [ \<Security >](security-of-basichttpbinding.md) alt öğesinin mode özniteliği değerinden `None`farklı bir değere ayarlanarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="f0d85-201">Varsayılan olarak bir "metin" ileti kodlaması ve UTF-8 metin kodlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0d85-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d85-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0d85-202">Example</span></span>  
 <span data-ttu-id="f0d85-203">Aşağıdaki örnek, ilk ve ikinci nesil <xref:System.ServiceModel.NetHttpBinding> Web Hizmetleri ile HTTP iletişimi ve en fazla birlikte çalışabilirlik sağlayan öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-203">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="f0d85-204">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="f0d85-205">Bağlama türü, `binding` `<endpoint>` öğesinin özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="f0d85-206">Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="f0d85-207">Uç noktanın, hizmetin aşağıdaki yapılandırma kodunda gösterildiği gibi, `bindingConfiguration` `<endpoint>` öğesinin özniteliğini kullanarak bağlama yapılandırmasına adı ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f0d85-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0d85-208">Example</span></span>  
 <span data-ttu-id="f0d85-209">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f0d85-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f0d85-210">Önceki örnekteki işlevsellik, bindingConfiguration bitiş noktası adresinden ve bağlamadan adından kaldırılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0d85-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
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
  
 <span data-ttu-id="f0d85-211">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="f0d85-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d85-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d85-212">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="f0d85-213">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0d85-213">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f0d85-214">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f0d85-214">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f0d85-215">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0d85-215">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f0d85-216">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f0d85-216">\<binding></span></span>](../../../misc/binding.md)
