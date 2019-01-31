---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 83cad6af4d00f04cd53e5e4b064fe768647956d1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277764"
---
# <a name="wshttpbinding"></a><span data-ttu-id="b2501-101">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b2501-101">\<wsHttpBinding></span></span>
<span data-ttu-id="b2501-102">Uygun olmayan yönlü Hizmet sözleşmeleri için güvenli, güvenilir ve birlikte çalışabilen bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2501-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="b2501-103">Bağlama aşağıdaki belirtimler uygular: WS-Reliable Mesajlaşma için güvenilirlik ve WS-güvenlik ileti güvenliği ve kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="b2501-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="b2501-104">HTTP taşıma ve ileti kodlama ise metin/XML kodlama.</span><span class="sxs-lookup"><span data-stu-id="b2501-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
 <span data-ttu-id="b2501-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2501-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2501-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b2501-106">\<bindings></span></span>  
<span data-ttu-id="b2501-107">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b2501-107">\<wsHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2501-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2501-108">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2501-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2501-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b2501-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2501-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2501-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2501-111">Attributes</span></span>  
  
|<span data-ttu-id="b2501-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2501-112">Attribute</span></span>|<span data-ttu-id="b2501-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2501-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2501-114">allowCookies</span><span class="sxs-lookup"><span data-stu-id="b2501-114">allowCookies</span></span>|<span data-ttu-id="b2501-115">İstemci tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b2501-115">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b2501-116">Varsayılan olarak yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="b2501-116">The default is false.</span></span><br /><br /> <span data-ttu-id="b2501-117">Tanımlama bilgileri kullanan ASMX Web Hizmetleri ile etkileşim kurduğunuzda bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2501-117">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="b2501-118">Bu şekilde, sunucudan döndürülen tanımlama bilgilerini aydaki hizmet için tüm istemci isteklerini otomatik olarak kopyalanır emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2501-118">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="b2501-119">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="b2501-119">bypassProxyOnLocal</span></span>|<span data-ttu-id="b2501-120">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b2501-120">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b2501-121">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b2501-121">The default is `false`.</span></span>|  
|<span data-ttu-id="b2501-122">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="b2501-122">closeTimeout</span></span>|<span data-ttu-id="b2501-123">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2501-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b2501-124">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b2501-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b2501-125">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b2501-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b2501-126">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="b2501-126">hostnameComparisonMode</span></span>|<span data-ttu-id="b2501-127">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2501-127">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b2501-128">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2501-128">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b2501-129">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="b2501-129">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="b2501-130">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="b2501-130">maxBufferPoolSize</span></span>|<span data-ttu-id="b2501-131">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b2501-131">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b2501-132">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b2501-132">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="b2501-133">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2501-133">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b2501-134">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2501-134">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="b2501-135">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="b2501-135">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="b2501-136">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="b2501-136">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="b2501-137">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="b2501-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="b2501-138">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b2501-138">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b2501-139">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b2501-139">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="b2501-140">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2501-140">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b2501-141">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b2501-141">The default is 65536.</span></span>|  
|<span data-ttu-id="b2501-142">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="b2501-142">messageEncoding</span></span>|<span data-ttu-id="b2501-143">İletisini kodlamak için kullanılan kodlayıcıya tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2501-143">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b2501-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b2501-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b2501-145">-Metni: Bir metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2501-145">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b2501-146">-Mtom: İleti Aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2501-146">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="b2501-147">-Metin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b2501-147">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="b2501-148">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="b2501-148">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="b2501-149">name</span><span class="sxs-lookup"><span data-stu-id="b2501-149">name</span></span>|<span data-ttu-id="b2501-150">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b2501-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b2501-151">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b2501-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b2501-152">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="b2501-152">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b2501-153">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b2501-153">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="b2501-154">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="b2501-154">openTimeout</span></span>|<span data-ttu-id="b2501-155">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2501-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b2501-156">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b2501-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b2501-157">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b2501-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b2501-158">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="b2501-158">proxyAddress</span></span>|<span data-ttu-id="b2501-159">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="b2501-159">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b2501-160">Varsa `useSystemWebProxy` olduğu `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="b2501-160">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b2501-161">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b2501-161">The default is `null`.</span></span>|  
|<span data-ttu-id="b2501-162">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="b2501-162">receiveTimeout</span></span>|<span data-ttu-id="b2501-163">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2501-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b2501-164">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b2501-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b2501-165">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b2501-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b2501-166">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="b2501-166">sendTimeout</span></span>|<span data-ttu-id="b2501-167">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2501-167">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b2501-168">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b2501-168">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b2501-169">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b2501-169">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b2501-170">textEncoding</span><span class="sxs-lookup"><span data-stu-id="b2501-170">textEncoding</span></span>|<span data-ttu-id="b2501-171">Bağlamadaki yayma iletileri için kullanılacak kodlama karakter kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2501-171">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b2501-172">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b2501-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b2501-173">-   UnicodeFffeTextEncoding: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="b2501-173">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b2501-174">-   Utf16TextEncoding: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="b2501-174">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="b2501-175">-   Utf8TextEncoding: 8-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="b2501-175">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b2501-176">Utf8TextEncoding varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b2501-176">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="b2501-177">Bu öznitelik türünde <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b2501-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="b2501-178">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="b2501-178">transactionFlow</span></span>|<span data-ttu-id="b2501-179">WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b2501-179">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b2501-180">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b2501-180">The default is `false`.</span></span>|  
|<span data-ttu-id="b2501-181">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="b2501-181">useDefaultWebProxy</span></span>|<span data-ttu-id="b2501-182">Sistemin otomatik yapılandırılan HTTP Ara sunucusu kullanılıp kullanılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b2501-182">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b2501-183">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b2501-183">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2501-184">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2501-184">Child Elements</span></span>  
  
|<span data-ttu-id="b2501-185">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2501-185">Element</span></span>|<span data-ttu-id="b2501-186">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2501-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2501-187">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b2501-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="b2501-188">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2501-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="b2501-189">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b2501-189">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b2501-190">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="b2501-190">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b2501-191">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2501-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b2501-192">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b2501-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="b2501-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="b2501-193">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="b2501-194">Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2501-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2501-195">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2501-195">Parent Elements</span></span>  
  
|<span data-ttu-id="b2501-196">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2501-196">Element</span></span>|<span data-ttu-id="b2501-197">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2501-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2501-198">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b2501-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b2501-199">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="b2501-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2501-200">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2501-200">Remarks</span></span>  
 <span data-ttu-id="b2501-201">`WSHttpBinding` Benzer `BasicHttpBinding` ancak daha fazla Web hizmeti özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2501-201">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="b2501-202">HTTP aktarımı kullanır ve BasicHttpBinding, aynı ileti güvenliği sağlar, ancak ayrıca işlemleri, güvenilir Mesajlaşma ve WS-Addressing sağlar, ya da varsayılan olarak ya da mevcut bir tek bir denetim ayarı ile etkin.</span><span class="sxs-lookup"><span data-stu-id="b2501-202">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2501-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2501-203">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b2501-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2501-204">See also</span></span>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="b2501-205">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b2501-205">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b2501-206">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b2501-206">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2501-207">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b2501-207">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b2501-208">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b2501-208">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
