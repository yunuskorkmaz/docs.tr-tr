---
title: <wsHttpBinding>
description: ', WS-güvenilir mesajlaşma ve WS-Security uygulayan, çift yönlü olmayan hizmet sözleşmeleri için uygun olan güvenli, güvenilir, birlikte çalışabilen bir HTTP bağlaması tanımlar.'
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: d603f699145622cb1b70ecf99ea542572e841eac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243990"
---
# \<wsHttpBinding>
<span data-ttu-id="46b6f-102">Çift yönlü olmayan hizmet sözleşmeleri için uygun olan güvenli, güvenilir, birlikte çalışabilen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="46b6f-103">Bağlama aşağıdaki belirtimleri uygular: güvenilirlik için WS-güvenilir mesajlaşma ve ileti güvenliği ve kimlik doğrulaması için WS-Security.</span><span class="sxs-lookup"><span data-stu-id="46b6f-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="46b6f-104">Aktarım HTTP ve ileti kodlama metin/XML kodlanıyor.</span><span class="sxs-lookup"><span data-stu-id="46b6f-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="46b6f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="46b6f-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46b6f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="46b6f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="46b6f-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="46b6f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46b6f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46b6f-108">Attributes</span></span>  
  
|<span data-ttu-id="46b6f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="46b6f-109">Attribute</span></span>|<span data-ttu-id="46b6f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46b6f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46b6f-111">allowCookies</span><span class="sxs-lookup"><span data-stu-id="46b6f-111">allowCookies</span></span>|<span data-ttu-id="46b6f-112">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="46b6f-112">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="46b6f-113">Varsayılan değer false.</span><span class="sxs-lookup"><span data-stu-id="46b6f-113">The default is false.</span></span><br /><br /> <span data-ttu-id="46b6f-114">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b6f-114">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="46b6f-115">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b6f-115">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="46b6f-116">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="46b6f-116">bypassProxyOnLocal</span></span>|<span data-ttu-id="46b6f-117">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="46b6f-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="46b6f-118">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="46b6f-118">The default is `false`.</span></span>|  
|<span data-ttu-id="46b6f-119">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="46b6f-119">closeTimeout</span></span>|<span data-ttu-id="46b6f-120"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="46b6f-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="46b6f-121">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46b6f-122">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-122">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46b6f-123">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="46b6f-123">hostnameComparisonMode</span></span>|<span data-ttu-id="46b6f-124">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-124">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="46b6f-125">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="46b6f-125">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="46b6f-126">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="46b6f-126">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="46b6f-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="46b6f-127">maxBufferPoolSize</span></span>|<span data-ttu-id="46b6f-128">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="46b6f-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="46b6f-129">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="46b6f-129">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="46b6f-130">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="46b6f-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="46b6f-131">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="46b6f-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="46b6f-132">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b6f-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="46b6f-133">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="46b6f-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="46b6f-134">Değerini</span><span class="sxs-lookup"><span data-stu-id="46b6f-134">maxReceivedMessageSize</span></span>|<span data-ttu-id="46b6f-135">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="46b6f-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="46b6f-136">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="46b6f-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="46b6f-137">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b6f-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="46b6f-138">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-138">The default is 65536.</span></span>|  
|<span data-ttu-id="46b6f-139">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="46b6f-139">messageEncoding</span></span>|<span data-ttu-id="46b6f-140">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-140">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="46b6f-141">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46b6f-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46b6f-142">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="46b6f-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="46b6f-143">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="46b6f-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="46b6f-144">-Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-144">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="46b6f-145">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="46b6f-146">name</span><span class="sxs-lookup"><span data-stu-id="46b6f-146">name</span></span>|<span data-ttu-id="46b6f-147">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="46b6f-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="46b6f-148">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46b6f-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="46b6f-149">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="46b6f-150">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="46b6f-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="46b6f-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="46b6f-151">openTimeout</span></span>|<span data-ttu-id="46b6f-152">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="46b6f-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="46b6f-153">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46b6f-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46b6f-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="46b6f-155">proxyAddress</span></span>|<span data-ttu-id="46b6f-156">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="46b6f-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="46b6f-157">`useSystemWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="46b6f-157">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="46b6f-158">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="46b6f-158">The default is `null`.</span></span>|  
|<span data-ttu-id="46b6f-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="46b6f-159">receiveTimeout</span></span>|<span data-ttu-id="46b6f-160"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="46b6f-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="46b6f-161">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46b6f-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46b6f-163">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="46b6f-163">sendTimeout</span></span>|<span data-ttu-id="46b6f-164"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="46b6f-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="46b6f-165">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46b6f-166">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46b6f-167">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="46b6f-167">textEncoding</span></span>|<span data-ttu-id="46b6f-168">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-168">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="46b6f-169">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46b6f-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46b6f-170">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="46b6f-170">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="46b6f-171">-Utf16TextEncoding: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="46b6f-171">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="46b6f-172">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="46b6f-172">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="46b6f-173">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-173">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="46b6f-174">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-174">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="46b6f-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="46b6f-175">transactionFlow</span></span>|<span data-ttu-id="46b6f-176">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="46b6f-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="46b6f-177">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="46b6f-177">The default is `false`.</span></span>|  
|<span data-ttu-id="46b6f-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="46b6f-178">useDefaultWebProxy</span></span>|<span data-ttu-id="46b6f-179">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="46b6f-179">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="46b6f-180">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="46b6f-180">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46b6f-181">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46b6f-181">Child Elements</span></span>  
  
|<span data-ttu-id="46b6f-182">Öğe</span><span class="sxs-lookup"><span data-stu-id="46b6f-182">Element</span></span>|<span data-ttu-id="46b6f-183">Description</span><span class="sxs-lookup"><span data-stu-id="46b6f-183">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="46b6f-184">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-184">Defines the security settings for the binding.</span></span> <span data-ttu-id="46b6f-185">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-185">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="46b6f-186">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-186">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="46b6f-187">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="46b6f-187">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="46b6f-188">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-188">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46b6f-189">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46b6f-189">Parent Elements</span></span>  
  
|<span data-ttu-id="46b6f-190">Öğe</span><span class="sxs-lookup"><span data-stu-id="46b6f-190">Element</span></span>|<span data-ttu-id="46b6f-191">Description</span><span class="sxs-lookup"><span data-stu-id="46b6f-191">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="46b6f-192">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="46b6f-192">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46b6f-193">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46b6f-193">Remarks</span></span>  
 <span data-ttu-id="46b6f-194">, `WSHttpBinding` Öğesine benzerdir `BasicHttpBinding` ancak daha fazla Web hizmeti özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-194">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="46b6f-195">HTTP aktarımını kullanır ve, BasicHttpBinding gibi ileti güvenliği sağlar, ancak varsayılan olarak etkinleştirilmiş veya tek bir denetim ayarıyla kullanılabilen işlemler, güvenilir mesajlaşma ve WS-Addressing işlemleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="46b6f-195">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46b6f-196">Örnek</span><span class="sxs-lookup"><span data-stu-id="46b6f-196">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46b6f-197">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46b6f-197">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="46b6f-198">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="46b6f-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="46b6f-199">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="46b6f-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="46b6f-200">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="46b6f-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
