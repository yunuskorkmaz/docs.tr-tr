---
title: '&lt;wsDualHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33c94271dee0fa9fbcdd48b44b983f650f87a6bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwsdualhttpbindinggt"></a><span data-ttu-id="d50b0-102">&lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d50b0-102">&lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="d50b0-103">Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli, güvenilir ve birlikte çalışabilir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-103">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="d50b0-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d50b0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d50b0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d50b0-105">\<bindings></span></span>  
<span data-ttu-id="d50b0-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d50b0-106">\<wsDualHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50b0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d50b0-107">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d50b0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d50b0-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="d50b0-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d50b0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d50b0-110">Attributes</span></span>  
  
|<span data-ttu-id="d50b0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d50b0-111">Attribute</span></span>|<span data-ttu-id="d50b0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d50b0-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="d50b0-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="d50b0-114">Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d50b0-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="d50b0-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-115">The default is `false`.</span></span>|  
|<span data-ttu-id="d50b0-116">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="d50b0-116">clientBaseAddress</span></span>|<span data-ttu-id="d50b0-117">İstemci yanıt iletileri hizmetinden dinler temel adresini ayarlar URI.</span><span class="sxs-lookup"><span data-stu-id="d50b0-117">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="d50b0-118">Belirtilmişse, bu adres (artı bir başına-channelGUID) dinlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-118">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="d50b0-119">Değer belirtilmezse, istemci taban adresi aktarım özgü bir şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d50b0-119">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="d50b0-120">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-120">The default is `null`.</span></span>|  
|<span data-ttu-id="d50b0-121">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d50b0-121">closeTimeout</span></span>|<span data-ttu-id="d50b0-122">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d50b0-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d50b0-123">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d50b0-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-124">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d50b0-125">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d50b0-125">hostnameComparisonMode</span></span>|<span data-ttu-id="d50b0-126">URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-126">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="d50b0-127">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-127">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="d50b0-128">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-128">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="d50b0-129">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d50b0-129">maxBufferPoolSize</span></span>|<span data-ttu-id="d50b0-130">Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d50b0-130">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d50b0-131">Varsayılan 524.288 (512 * 1024) bayttır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-131">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="d50b0-132">Pek çok bölümü Windows Communication Foundation (WCF) arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d50b0-132">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d50b0-133">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-133">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d50b0-134">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="d50b0-134">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d50b0-135">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="d50b0-135">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="d50b0-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d50b0-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="d50b0-137">Bu bağlama ile yapılandırılan kanalda alınan başlıkları dahil bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d50b0-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d50b0-138">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="d50b0-139">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d50b0-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d50b0-140">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-140">The default is 65536.</span></span>|  
|<span data-ttu-id="d50b0-141">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="d50b0-141">messageEncoding</span></span>|<span data-ttu-id="d50b0-142">İleti kodlanması için kullanılan Kodlayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-142">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="d50b0-143">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d50b0-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d50b0-144">-Metin: metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d50b0-144">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="d50b0-145">-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d50b0-145">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="d50b0-146">-Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-146">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="d50b0-147">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-147">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="d50b0-148">name</span><span class="sxs-lookup"><span data-stu-id="d50b0-148">name</span></span>|<span data-ttu-id="d50b0-149">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="d50b0-149">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d50b0-150">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-150">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d50b0-151">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-151">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d50b0-152">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d50b0-152">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="d50b0-153">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d50b0-153">openTimeout</span></span>|<span data-ttu-id="d50b0-154">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d50b0-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d50b0-155">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d50b0-156">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-156">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d50b0-157">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="d50b0-157">proxyAddress</span></span>|<span data-ttu-id="d50b0-158">HTTP proxy adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="d50b0-158">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="d50b0-159">Varsa `useDefaultWebProxy` olan `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="d50b0-159">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="d50b0-160">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-160">The default is `null`.</span></span>|  
|<span data-ttu-id="d50b0-161">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d50b0-161">receiveTimeout</span></span>|<span data-ttu-id="d50b0-162">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d50b0-162">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d50b0-163">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-163">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d50b0-164">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-164">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d50b0-165">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="d50b0-165">sendTimeout</span></span>|<span data-ttu-id="d50b0-166">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d50b0-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d50b0-167">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d50b0-168">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-168">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="d50b0-169">textEncoding</span><span class="sxs-lookup"><span data-stu-id="d50b0-169">textEncoding</span></span>|<span data-ttu-id="d50b0-170">Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-170">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d50b0-171">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d50b0-171">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d50b0-172">-BigEndianUnicode: Unicode BigEndian kodlama.</span><span class="sxs-lookup"><span data-stu-id="d50b0-172">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="d50b0-173">-Unicode: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="d50b0-173">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="d50b0-174">-UTF8: 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="d50b0-174">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d50b0-175">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d50b0-175">The default is UTF8.</span></span> <span data-ttu-id="d50b0-176">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-176">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="d50b0-177">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="d50b0-177">transactionFlow</span></span>|<span data-ttu-id="d50b0-178">Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d50b0-178">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="d50b0-179">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-179">The default is `false`.</span></span>|  
|<span data-ttu-id="d50b0-180">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="d50b0-180">useDefaultWebProxy</span></span>|<span data-ttu-id="d50b0-181">Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d50b0-181">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="d50b0-182">Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlanmamış) bu özniteliği ise `true`.</span><span class="sxs-lookup"><span data-stu-id="d50b0-182">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="d50b0-183">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d50b0-184">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b0-184">Child Elements</span></span>  
  
|<span data-ttu-id="d50b0-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="d50b0-185">Element</span></span>|<span data-ttu-id="d50b0-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b0-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d50b0-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d50b0-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|<span data-ttu-id="d50b0-188">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="d50b0-189">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-189">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="d50b0-190">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="d50b0-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="d50b0-191">Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d50b0-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d50b0-192">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d50b0-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="d50b0-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="d50b0-193">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="d50b0-194">Güvenilir oturumlar kanal uç noktaları arasında kurulan olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d50b0-195">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d50b0-195">Parent Elements</span></span>  
  
|<span data-ttu-id="d50b0-196">Öğe</span><span class="sxs-lookup"><span data-stu-id="d50b0-196">Element</span></span>|<span data-ttu-id="d50b0-197">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d50b0-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d50b0-198">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d50b0-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="d50b0-199">Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d50b0-200">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d50b0-200">Remarks</span></span>  
 <span data-ttu-id="d50b0-201">`WSDualHttpBinding` Web hizmeti protokolleri aynı destek sağlayan `WSHttpBinding`, ancak çift yönlü sözleşmeler ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="d50b0-201">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="d50b0-202">`WSDualHttpBinding`yalnızca SOAP Güvenliği destekler ve güvenilir Mesajlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-202">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="d50b0-203">Bu bağlama istemci hizmeti için bir geri çağırma uç noktası sağlayan ortak bir URI sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-203">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="d50b0-204">Bu tarafından sağlanan `clientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d50b0-204">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="d50b0-205">Bir çift bağlama hizmeti istemcinin IP adresini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-205">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="d50b0-206">İstemci, yalnızca Hizmetleri güvenleri bağladığı emin olmak için güvenlik kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-206">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="d50b0-207">Bu bağlama, güvenilir bir şekilde bir veya daha fazla SOAP aracılar iletişim kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d50b0-207">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="d50b0-208">Varsayılan olarak, WS-ReliableMessaging çalışma zamanı yığın güvenilirlik, WS-güvenlik ileti güvenliği ve kimlik doğrulama, ileti teslimi, HTTP için bu bağlama oluşturur ve bir Text/XML ileti kodlama.</span><span class="sxs-lookup"><span data-stu-id="d50b0-208">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d50b0-209">Örnek</span><span class="sxs-lookup"><span data-stu-id="d50b0-209">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d50b0-210">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d50b0-210">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [<span data-ttu-id="d50b0-211">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d50b0-211">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d50b0-212">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d50b0-212">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d50b0-213">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d50b0-213">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d50b0-214">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d50b0-214">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
