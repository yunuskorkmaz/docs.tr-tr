---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3025eec9c01d325d7d00a7355ff908eb1e19e410
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="e3be4-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e3be4-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="e3be4-103">Türetilen bir güvenli ve birlikte çalışabilir bağlama [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve Federasyon güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="e3be4-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="e3be4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3be4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3be4-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e3be4-105">\<bindings></span></span>  
<span data-ttu-id="e3be4-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e3be4-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3be4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3be4-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3be4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3be4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3be4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3be4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3be4-110">Attributes</span></span>  
  
|<span data-ttu-id="e3be4-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3be4-111">Attribute</span></span>|<span data-ttu-id="e3be4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3be4-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="e3be4-113">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e3be4-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="e3be4-115">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e3be4-116">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e3be4-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="e3be4-118">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="e3be4-119">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e3be4-120">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="e3be4-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e3be4-121">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="e3be4-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e3be4-122">Varsayılan 524.288 (512 \* 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="e3be4-123">Birçok bölümlerini [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3be4-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="e3be4-124">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e3be4-125">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="e3be4-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e3be4-126">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="e3be4-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e3be4-127">Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="e3be4-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e3be4-128">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="e3be4-129">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3be4-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e3be4-130">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="e3be4-131">İleti kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3be4-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="e3be4-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e3be4-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e3be4-133">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3be4-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="e3be4-134">-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3be4-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="e3be4-135">Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="e3be4-136">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="e3be4-137">Bağlama yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="e3be4-137">The configuration name of the binding.</span></span> <span data-ttu-id="e3be4-138">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e3be4-139">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e3be4-140">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e3be4-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e3be4-141">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e3be4-142">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e3be4-143">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="e3be4-144">Gizlilik bildirimi bulunduğu olduğu URI.</span><span class="sxs-lookup"><span data-stu-id="e3be4-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="e3be4-145">Geçerli gizlilik bildirimi sürümü.</span><span class="sxs-lookup"><span data-stu-id="e3be4-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="e3be4-146">HTTP proxy adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="e3be4-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="e3be4-147">Varsa `useDefaultWebProxy` olan `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="e3be4-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="e3be4-148">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e3be4-149">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e3be4-150">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e3be4-151">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e3be4-152">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e3be4-153">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e3be4-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e3be4-155">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e3be4-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e3be4-156">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e3be4-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e3be4-157">-BigEndianUnicode: Unicode Big Endian'ya kodlaması.</span><span class="sxs-lookup"><span data-stu-id="e3be4-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="e3be4-158">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="e3be4-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="e3be4-159">-UTF8: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="e3be4-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e3be4-160">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-160">The default is UTF8.</span></span> <span data-ttu-id="e3be4-161">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="e3be4-162">Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e3be4-163">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="e3be4-164">Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="e3be4-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="e3be4-165">Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlanmamış) bu özniteliği ise `true`.</span><span class="sxs-lookup"><span data-stu-id="e3be4-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="e3be4-166">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3be4-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3be4-167">Child Elements</span></span>  
  
|<span data-ttu-id="e3be4-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3be4-168">Element</span></span>|<span data-ttu-id="e3be4-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3be4-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3be4-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e3be4-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="e3be4-171">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3be4-171">Defines the security settings for the message.</span></span> <span data-ttu-id="e3be4-172">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="e3be4-173">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="e3be4-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="e3be4-174">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3be4-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e3be4-175">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e3be4-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="e3be4-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="e3be4-176">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="e3be4-177">Güvenilir oturumlar kanal uç noktaları arasında kurulan olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3be4-178">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3be4-178">Parent Elements</span></span>  
  
|<span data-ttu-id="e3be4-179">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3be4-179">Element</span></span>|<span data-ttu-id="e3be4-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3be4-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3be4-181">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e3be4-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e3be4-182">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3be4-183">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3be4-183">Remarks</span></span>  
 <span data-ttu-id="e3be4-184">Federasyon kimlikleri birden çok kuruluşlar veya kimlik doğrulama ve yetkilendirme için güven etki alanları paylaşma olanağı ' dir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="e3be4-185">Başka bir kimlik temsili bir güven etki alanından eşlemek için WS-Trust protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3be4-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="e3be4-186">Karma mod güvenliği yanı sıra SOAP Güvenliği Federasyon HTTP bağlama destekler, ancak taşıma güvenliği desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="e3be4-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="e3be4-187">Bu bağlama ile yapılandırılan hizmetler HTTP aktarımı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3be4-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="e3be4-188">Daha fazla bilgi için bkz: [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e3be4-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3be4-189">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3be4-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3be4-190">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3be4-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="e3be4-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e3be4-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="e3be4-192">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e3be4-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e3be4-193">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3be4-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e3be4-194">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="e3be4-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e3be4-195">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e3be4-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
