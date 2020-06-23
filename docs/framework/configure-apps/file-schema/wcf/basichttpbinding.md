---
title: <basicHttpBinding>
description: Bir WCF hizmetinin WS-ı temel profili 1,1 ile uyumlu hizmetlerle iletişim kurmak üzere uç noktaları yapılandırmak ve kullanıma sunmak için kullanabileceği bir bağlamayı tanımlar.
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: 5b2ce1973966468107d7aa4de545a976c67b13ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244029"
---
# \<basicHttpBinding>
<span data-ttu-id="68440-102">Windows Communication Foundation (WCF) hizmetinin, ASMX tabanlı Web Hizmetleri ve istemcilerle ve WS-ı temel profili 1,1 ile uyumlu diğer hizmetlerle iletişim kurabilen uç noktaları yapılandırmak ve ortaya çıkarmak için kullanabileceği bir bağlamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68440-102">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<basicHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="68440-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="68440-103">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68440-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68440-104">Attributes and Elements</span></span>  
 <span data-ttu-id="68440-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68440-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68440-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68440-106">Attributes</span></span>  
  
|<span data-ttu-id="68440-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68440-107">Attribute</span></span>|<span data-ttu-id="68440-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68440-108">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="68440-109">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="68440-109">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="68440-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="68440-110">The default is `false`.</span></span><br /><br /> <span data-ttu-id="68440-111">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68440-111">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="68440-112">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68440-112">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="68440-113">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="68440-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="68440-114">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="68440-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="68440-115">Bir Internet kaynağı, yerel bir adresi varsa yereldir.</span><span class="sxs-lookup"><span data-stu-id="68440-115">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="68440-116">Yerel bir adres, aynı bilgisayarda, yerel LAN veya intranette bulunan ve sözdizimi ve sözdizimi, sözdizimi, URI 'Ler ve bir nokta (.) ile tanımlanır `http://webserver/` `http://localhost/` .</span><span class="sxs-lookup"><span data-stu-id="68440-116">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="68440-117">Bu özniteliğin ayarlanması, BasicHttpBinding ile yapılandırılan uç noktaların yerel kaynaklara erişirken proxy sunucusunu kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="68440-117">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="68440-118">Bu öznitelik ise `true` , yerel Internet kaynaklarına yönelik istekler proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="68440-118">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="68440-119">İstemcilerin, bu öznitelik olarak ayarlandığında aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini isterseniz ana bilgisayar adını (localhost yerine) kullanın `true` .</span><span class="sxs-lookup"><span data-stu-id="68440-119">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="68440-120">Bu öznitelik olduğunda `false` , tüm Internet istekleri proxy sunucu aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="68440-120">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="68440-121"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="68440-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="68440-122">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="68440-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68440-123">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68440-123">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="68440-124">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="68440-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="68440-125">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="68440-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="68440-126">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="68440-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="68440-127">Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="68440-127">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="68440-128">Varsayılan değer 524288 (0X80000) bayttır.</span><span class="sxs-lookup"><span data-stu-id="68440-128">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="68440-129">Arabellek Yöneticisi, arabellek havuzu kullanarak arabellek kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="68440-129">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="68440-130">Arabellekleri, kanalın dışına geldiklerinde hizmete göre işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="68440-130">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="68440-131">Arabellek havuzunda ileti yükünü işlemek için yeterli bellek yoksa, arabellek yöneticisinin CLR yığınından ek bellek ayırması gerekir ve bu da çöp toplama yükünü artırır.</span><span class="sxs-lookup"><span data-stu-id="68440-131">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="68440-132">CLR atık yığınından kapsamlı ayırma, arabellek havuzu boyutunun çok küçük olduğunu ve bu öznitelik tarafından belirtilen sınırı artırarak performansın daha büyük bir ayırma ile iyileşebileceğinin göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="68440-132">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="68440-133">Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="68440-133">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="68440-134">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="68440-134">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="68440-135">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="68440-135">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="68440-136">İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor.</span><span class="sxs-lookup"><span data-stu-id="68440-136">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="68440-137">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="68440-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="68440-138">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="68440-138">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="68440-139">SOAP iletisini kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68440-139">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="68440-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="68440-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="68440-141">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="68440-141">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="68440-142">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="68440-142">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="68440-143">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="68440-143">The default is Text.</span></span> <span data-ttu-id="68440-144">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="68440-144">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="68440-145">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="68440-145">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="68440-146">Bu değer, aynı türde bağlamalar arasında benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68440-146">This value should be unique among bindings of the same type.</span></span> <span data-ttu-id="68440-147">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="68440-147">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="68440-148">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="68440-148">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="68440-149">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="68440-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="68440-150">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="68440-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68440-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68440-151">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="68440-152">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="68440-152">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="68440-153">, `useSystemWebProxy` Olarak ayarlandıysa `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="68440-153">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="68440-154">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="68440-154">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="68440-155"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="68440-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="68440-156">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="68440-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68440-157">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68440-157">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="68440-158"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="68440-158">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="68440-159">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="68440-159">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="68440-160">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68440-160">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="68440-161">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="68440-161">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="68440-162">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="68440-162">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="68440-163">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="68440-163">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="68440-164">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="68440-164">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="68440-165">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="68440-165">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="68440-166">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="68440-166">The default is UTF8.</span></span> <span data-ttu-id="68440-167">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="68440-167">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="68440-168"><xref:System.ServiceModel.TransferMode>İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt üzerinde akış yapılıp yapılmayacağını belirten geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="68440-168">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="68440-169">Varsa, sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="68440-169">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="68440-170">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="68440-170">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68440-171">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68440-171">Child Elements</span></span>  
  
|<span data-ttu-id="68440-172">Öğe</span><span class="sxs-lookup"><span data-stu-id="68440-172">Element</span></span>|<span data-ttu-id="68440-173">Description</span><span class="sxs-lookup"><span data-stu-id="68440-173">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="68440-174">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68440-174">Defines the security settings for the binding.</span></span> <span data-ttu-id="68440-175">Bu öğe türündedir <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="68440-175">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="68440-176">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68440-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="68440-177">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="68440-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68440-178">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68440-178">Parent Elements</span></span>  
  
|<span data-ttu-id="68440-179">Öğe</span><span class="sxs-lookup"><span data-stu-id="68440-179">Element</span></span>|<span data-ttu-id="68440-180">Description</span><span class="sxs-lookup"><span data-stu-id="68440-180">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="68440-181">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="68440-181">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68440-182">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68440-182">Remarks</span></span>  
 <span data-ttu-id="68440-183">BasicHttpBinding, SOAP 1,1 iletileri göndermek için taşıma olarak HTTP kullanır.</span><span class="sxs-lookup"><span data-stu-id="68440-183">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="68440-184">Hizmet, ASMX istemcilerinin tükettiği gibi WS-ı BP 1,1 'e uygun uç noktaları ortaya çıkarmak için bu bağlamayı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68440-184">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="68440-185">Benzer şekilde, istemci, Web hizmeti ile 1,1 uyumlu bir uç nokta (ASMX Web Hizmetleri veya BasicHttpBinding ile yapılandırılmış hizmetler gibi) kullanan hizmetlerle iletişim kurmak için BasicHttpBinding 'i kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68440-185">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="68440-186">Güvenlik varsayılan olarak kapalıdır, ancak [\<security>](security-of-basichttpbinding.md) alt öğenin mode özniteliği değerinden farklı bir değere ayarlanarak eklenebilir `None` .</span><span class="sxs-lookup"><span data-stu-id="68440-186">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="68440-187">Varsayılan olarak bir "metin" ileti kodlaması ve UTF-8 metin kodlaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="68440-187">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68440-188">Örnek</span><span class="sxs-lookup"><span data-stu-id="68440-188">Example</span></span>  
 <span data-ttu-id="68440-189">Aşağıdaki örnek, <xref:System.ServiceModel.BasicHttpBinding> ilk ve ikinci nesil Web Hizmetleri Ile http iletişimi ve en fazla birlikte çalışabilirlik sağlayan öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="68440-189">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="68440-190">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="68440-190">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="68440-191">Bağlama türü, öğesinin özniteliği kullanılarak belirtilir `binding` `<endpoint>` .</span><span class="sxs-lookup"><span data-stu-id="68440-191">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="68440-192">Temel bağlamayı yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68440-192">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="68440-193">Uç noktanın, `bindingConfiguration` `<endpoint>` hizmetin aşağıdaki yapılandırma kodunda gösterildiği gibi, öğesinin özniteliğini kullanarak bağlama yapılandırmasına adı ile başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68440-193">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="68440-194">Örnek</span><span class="sxs-lookup"><span data-stu-id="68440-194">Example</span></span>  
 <span data-ttu-id="68440-195">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="68440-195">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="68440-196">Önceki örnekteki işlevsellik, bindingConfiguration bitiş noktası adresinden ve bağlamadan adından kaldırılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="68440-196">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="68440-197">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="68440-197">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68440-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68440-198">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="68440-199">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="68440-199">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="68440-200">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="68440-200">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="68440-201">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="68440-201">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
