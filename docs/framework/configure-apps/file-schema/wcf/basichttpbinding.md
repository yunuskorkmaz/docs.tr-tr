---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7842efe074d5487a5917e7ee669027a420d9d713
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="24299-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="24299-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="24299-103">Bağlama temsil eder, bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet yapılandırmak ve ASMX tabanlı Web hizmetlerinde ve istemcilerin ve WS uygun diğer hizmetler ile iletişim kurabildiğinden uç noktalarını kullanıma sunmak için kullanabilirsiniz-ı temel Profil 1.1.</span><span class="sxs-lookup"><span data-stu-id="24299-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="24299-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="24299-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24299-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="24299-105">\<bindings></span></span>  
<span data-ttu-id="24299-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="24299-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24299-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24299-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24299-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24299-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24299-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24299-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24299-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24299-110">Attributes</span></span>  
  
|<span data-ttu-id="24299-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="24299-111">Attribute</span></span>|<span data-ttu-id="24299-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24299-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="24299-113">İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="24299-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="24299-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="24299-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="24299-115">Tanımlama bilgileri kullan ASMX Web Hizmetleri ile etkileşim kurarken, bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24299-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="24299-116">Bu şekilde, sunucudan döndürülen tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalandığından emin olabilir.</span><span class="sxs-lookup"><span data-stu-id="24299-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="24299-117">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="24299-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="24299-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="24299-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="24299-119">Yerel bir adres varsa, yerel bir Internet kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="24299-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="24299-120">Yerel bir adres aynı bilgisayarda, yerel ağ veya intranet ve, sözdizimsel olarak, URI "http://webserver/" ve "http://localhost/" olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir.</span><span class="sxs-lookup"><span data-stu-id="24299-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="24299-121">Bu öznitelik ayarlama BasicHttpBinding ile yapılandırılmış uç noktaları yerel kaynaklara erişirken proxy sunucusu kullanıp kullanmayacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="24299-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="24299-122">Bu öznitelik değilse `true`, yerel Internet kaynakların isteklerine proxy sunucusunu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="24299-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="24299-123">Bu öznitelik ayarlandığında hizmetler için aynı makinede konuşurken bir proxy üzerinden gitmek için istemcilerin istiyorsanız konak adı (localhost yerine) kullanın `true`.</span><span class="sxs-lookup"><span data-stu-id="24299-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="24299-124">Bu öznitelik olduğunda `false`, proxy sunucu üzerinden yapılan tüm Internet istekleri.</span><span class="sxs-lookup"><span data-stu-id="24299-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="24299-125">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="24299-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="24299-126">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="24299-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24299-127">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="24299-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="24299-128">Bu bağlama tarafından işlenen iletiler için kullanılan SOAP sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="24299-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="24299-129">Soap11 yalnızca geçerli değeridir.</span><span class="sxs-lookup"><span data-stu-id="24299-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="24299-130">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="24299-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="24299-131">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="24299-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="24299-132">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="24299-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="24299-133">Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan bellek miktarını belirten bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="24299-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="24299-134">Varsayılan değer 524288 (0x80000): bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="24299-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="24299-135">Arabellek Yöneticisi arabellek havuzu kullanarak arabellekleri kullanma maliyetini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="24299-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="24299-136">Kanal dışında geldiğinizde arabellekleri hizmeti tarafından iletilerini işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24299-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="24299-137">İleti yükü işlemek için arabellek havuzunda yeterli bellek yoksa, arabellek Yöneticisi atık toplama yükünü artırır CLR yığınından ek bellek ayırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24299-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="24299-138">CLR çöp yığınına gelen kapsamlı ayırma arabellek havuzu boyutu çok küçük olduğunu ve bu özniteliği tarafından belirtilen sınırı artırarak performansı ile daha büyük bir ayırma geliştirilebilir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="24299-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="24299-139">Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirtir bir tamsayı değeri.</span><span class="sxs-lookup"><span data-stu-id="24299-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="24299-140">Varsayılan değer 65.536 bayttır.</span><span class="sxs-lookup"><span data-stu-id="24299-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="24299-141">Bu bağlama ile yapılandırılan kanalda alınan bir ileti için üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="24299-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="24299-142">İleti alıcı için çok büyük ise gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="24299-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="24299-143">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24299-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="24299-144">Varsayılan 65.536 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="24299-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="24299-145">SOAP iletisi kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24299-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="24299-146">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24299-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="24299-147">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="24299-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="24299-148">-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="24299-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="24299-149">Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="24299-149">The default is Text.</span></span> <span data-ttu-id="24299-150">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="24299-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="24299-151">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="24299-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="24299-152">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24299-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="24299-153">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="24299-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="24299-154">Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="24299-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="24299-155">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24299-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="24299-156">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="24299-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="24299-157">XML ad alanı bağlamanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="24299-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="24299-158">Varsayılan değer "http://tempuri.org/Bindings" dir.</span><span class="sxs-lookup"><span data-stu-id="24299-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="24299-159">Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="24299-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="24299-160">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="24299-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="24299-161">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="24299-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24299-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="24299-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="24299-163">HTTP proxy adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="24299-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="24299-164">Varsa `useSystemWebProxy` ayarlanır `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="24299-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="24299-165">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="24299-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="24299-166">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="24299-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="24299-167">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="24299-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24299-168">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="24299-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="24299-169">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="24299-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="24299-170">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="24299-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24299-171">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="24299-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="24299-172">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24299-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="24299-173">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24299-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="24299-174">-BigEndianUnicode: Unicode BigEndian kodlama.</span><span class="sxs-lookup"><span data-stu-id="24299-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="24299-175">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="24299-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="24299-176">-UTF8: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="24299-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="24299-177">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="24299-177">The default is UTF8.</span></span> <span data-ttu-id="24299-178">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="24299-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="24299-179">Geçerli bir <xref:System.ServiceModel.TransferMode> iletilerin ara belleğe veya bir istek veya yanıt akışı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="24299-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="24299-180">Otomatik yapılandırılan HTTP Proxy'si sisteminin kullanılması gerekip gerekmediğini, varsa belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="24299-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="24299-181">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="24299-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24299-182">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24299-182">Child Elements</span></span>  
  
|<span data-ttu-id="24299-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="24299-183">Element</span></span>|<span data-ttu-id="24299-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24299-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24299-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="24299-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="24299-186">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24299-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="24299-187">Bu öğe türünde <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="24299-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="24299-188">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="24299-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="24299-189">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24299-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="24299-190">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="24299-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24299-191">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24299-191">Parent Elements</span></span>  
  
|<span data-ttu-id="24299-192">Öğe</span><span class="sxs-lookup"><span data-stu-id="24299-192">Element</span></span>|<span data-ttu-id="24299-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24299-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24299-194">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="24299-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="24299-195">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="24299-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24299-196">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24299-196">Remarks</span></span>  
 <span data-ttu-id="24299-197">BasicHttpBinding HTTP SOAP 1.1 ileti göndermek için taşıma olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="24299-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="24299-198">Bir hizmet WS uygun uç noktalarını göstermek için bu bağlamayı kullanan-ı BP 1.1 ASMX istemcileri tüketen olanlar gibi.</span><span class="sxs-lookup"><span data-stu-id="24299-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="24299-199">Benzer şekilde, istemci BasicHttpBinding WS uygun uç noktalarını gösterme Hizmetleri ile iletişim kurmak için kullanabilir-ı BP 1.1 ASMX Web Hizmetleri veya BasicHttpBinding ile yapılandırılmış hizmetler gibi.</span><span class="sxs-lookup"><span data-stu-id="24299-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="24299-200">Güvenlik varsayılan olarak devre dışıdır, ancak mod özniteliği ayarıyla eklenebilir [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) alt öğesi dışında bir değere `None`.</span><span class="sxs-lookup"><span data-stu-id="24299-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="24299-201">Varsayılan kodlama "Metin" İleti kodlama ve UTF-8 metnini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24299-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24299-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="24299-202">Example</span></span>  
 <span data-ttu-id="24299-203">Aşağıdaki örnek kullanımını gösteren <xref:System.ServiceModel.BasicHttpBinding> , HTTP iletişimi ve maksimum birlikte çalışabilirliği ilk - ve second - generation ile Web hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="24299-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="24299-204">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="24299-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="24299-205">Bağlama türü kullanılarak belirtilen `binding` özniteliği `<endpoint>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="24299-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="24299-206">Temel bağlama yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24299-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="24299-207">Uç nokta bağlama yapılandırması adıyla kullanarak başvurmalıdır `bindingConfiguration` özniteliği `<endpoint>` hizmeti için aşağıdaki yapılandırma kodda gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="24299-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
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
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="24299-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="24299-208">Example</span></span>  
 <span data-ttu-id="24299-209">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24299-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="24299-210">Önceki örnekte işlevinden uç nokta adresi ve bağlama adı frm bindingConfiguration kaldırarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="24299-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="24299-211">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="24299-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24299-212">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24299-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="24299-213">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24299-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="24299-214">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24299-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="24299-215">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="24299-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="24299-216">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="24299-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
