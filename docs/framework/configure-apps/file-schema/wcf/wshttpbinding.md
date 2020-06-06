---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: a71ad2a2279eabbcf917df58d7bedec0e728f9e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140398"
---
# \<wsHttpBinding>
<span data-ttu-id="da4bb-101">Çift yönlü olmayan hizmet sözleşmeleri için uygun olan güvenli, güvenilir, birlikte çalışabilen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-101">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="da4bb-102">Bağlama aşağıdaki belirtimleri uygular: güvenilirlik için WS-güvenilir mesajlaşma ve ileti güvenliği ve kimlik doğrulaması için WS-Security.</span><span class="sxs-lookup"><span data-stu-id="da4bb-102">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="da4bb-103">Aktarım HTTP ve ileti kodlama metin/XML kodlanıyor.</span><span class="sxs-lookup"><span data-stu-id="da4bb-103">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="da4bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da4bb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da4bb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4bb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="da4bb-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="da4bb-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da4bb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da4bb-107">Attributes</span></span>  
  
|<span data-ttu-id="da4bb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="da4bb-108">Attribute</span></span>|<span data-ttu-id="da4bb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da4bb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da4bb-110">allowCookies</span><span class="sxs-lookup"><span data-stu-id="da4bb-110">allowCookies</span></span>|<span data-ttu-id="da4bb-111">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="da4bb-111">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="da4bb-112">Varsayılan değer false.</span><span class="sxs-lookup"><span data-stu-id="da4bb-112">The default is false.</span></span><br /><br /> <span data-ttu-id="da4bb-113">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4bb-113">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="da4bb-114">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4bb-114">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="da4bb-115">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="da4bb-115">bypassProxyOnLocal</span></span>|<span data-ttu-id="da4bb-116">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="da4bb-116">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="da4bb-117">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="da4bb-117">The default is `false`.</span></span>|  
|<span data-ttu-id="da4bb-118">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="da4bb-118">closeTimeout</span></span>|<span data-ttu-id="da4bb-119"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="da4bb-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="da4bb-120">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="da4bb-121">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-121">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="da4bb-122">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="da4bb-122">hostnameComparisonMode</span></span>|<span data-ttu-id="da4bb-123">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-123">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="da4bb-124">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="da4bb-124">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="da4bb-125">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="da4bb-125">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="da4bb-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="da4bb-126">maxBufferPoolSize</span></span>|<span data-ttu-id="da4bb-127">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="da4bb-127">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="da4bb-128">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="da4bb-128">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="da4bb-129">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="da4bb-129">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="da4bb-130">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4bb-130">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="da4bb-131">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da4bb-131">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="da4bb-132">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="da4bb-132">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="da4bb-133">Değerini</span><span class="sxs-lookup"><span data-stu-id="da4bb-133">maxReceivedMessageSize</span></span>|<span data-ttu-id="da4bb-134">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="da4bb-134">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="da4bb-135">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="da4bb-135">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="da4bb-136">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da4bb-136">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="da4bb-137">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-137">The default is 65536.</span></span>|  
|<span data-ttu-id="da4bb-138">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="da4bb-138">messageEncoding</span></span>|<span data-ttu-id="da4bb-139">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-139">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="da4bb-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="da4bb-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="da4bb-141">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="da4bb-141">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="da4bb-142">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="da4bb-142">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="da4bb-143">-Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-143">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="da4bb-144">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-144">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="da4bb-145">name</span><span class="sxs-lookup"><span data-stu-id="da4bb-145">name</span></span>|<span data-ttu-id="da4bb-146">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="da4bb-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="da4bb-147">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4bb-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="da4bb-148">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-148">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="da4bb-149">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="da4bb-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="da4bb-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="da4bb-150">openTimeout</span></span>|<span data-ttu-id="da4bb-151">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="da4bb-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="da4bb-152">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="da4bb-153">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="da4bb-154">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="da4bb-154">proxyAddress</span></span>|<span data-ttu-id="da4bb-155">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="da4bb-155">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="da4bb-156">`useSystemWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="da4bb-156">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="da4bb-157">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="da4bb-157">The default is `null`.</span></span>|  
|<span data-ttu-id="da4bb-158">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="da4bb-158">receiveTimeout</span></span>|<span data-ttu-id="da4bb-159"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="da4bb-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="da4bb-160">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="da4bb-161">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="da4bb-162">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="da4bb-162">sendTimeout</span></span>|<span data-ttu-id="da4bb-163"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="da4bb-163">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="da4bb-164">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-164">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="da4bb-165">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-165">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="da4bb-166">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="da4bb-166">textEncoding</span></span>|<span data-ttu-id="da4bb-167">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-167">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="da4bb-168">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="da4bb-168">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="da4bb-169">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="da4bb-169">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="da4bb-170">-Utf16TextEncoding: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="da4bb-170">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="da4bb-171">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="da4bb-171">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="da4bb-172">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-172">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="da4bb-173">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-173">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="da4bb-174">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="da4bb-174">transactionFlow</span></span>|<span data-ttu-id="da4bb-175">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="da4bb-175">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="da4bb-176">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="da4bb-176">The default is `false`.</span></span>|  
|<span data-ttu-id="da4bb-177">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="da4bb-177">useDefaultWebProxy</span></span>|<span data-ttu-id="da4bb-178">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="da4bb-178">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="da4bb-179">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="da4bb-179">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da4bb-180">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4bb-180">Child Elements</span></span>  
  
|<span data-ttu-id="da4bb-181">Öğe</span><span class="sxs-lookup"><span data-stu-id="da4bb-181">Element</span></span>|<span data-ttu-id="da4bb-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da4bb-182">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="da4bb-183">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-183">Defines the security settings for the binding.</span></span> <span data-ttu-id="da4bb-184">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-184">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="da4bb-185">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-185">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="da4bb-186">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="da4bb-186">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="da4bb-187">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-187">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da4bb-188">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4bb-188">Parent Elements</span></span>  
  
|<span data-ttu-id="da4bb-189">Öğe</span><span class="sxs-lookup"><span data-stu-id="da4bb-189">Element</span></span>|<span data-ttu-id="da4bb-190">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da4bb-190">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="da4bb-191">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="da4bb-191">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4bb-192">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da4bb-192">Remarks</span></span>  
 <span data-ttu-id="da4bb-193">, `WSHttpBinding` Öğesine benzerdir `BasicHttpBinding` ancak daha fazla Web hizmeti özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-193">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="da4bb-194">HTTP aktarımını kullanır ve, BasicHttpBinding gibi ileti güvenliği sağlar, ancak varsayılan olarak etkinleştirilmiş veya tek bir denetim ayarıyla kullanılabilen işlemler, güvenilir mesajlaşma ve WS-Addressing işlemleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4bb-194">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da4bb-195">Örnek</span><span class="sxs-lookup"><span data-stu-id="da4bb-195">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da4bb-196">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4bb-196">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="da4bb-197">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="da4bb-197">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="da4bb-198">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="da4bb-198">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="da4bb-199">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="da4bb-199">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
