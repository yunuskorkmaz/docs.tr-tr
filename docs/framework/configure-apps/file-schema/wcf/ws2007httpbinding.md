---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2fb9f7a16a360ddd61e6f8b935f928ddfdeb6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915250"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="e6f04-101">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6f04-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="e6f04-102"><xref:System.ServiceModel.WSHttpBinding.Security%2A> ,<xref:System.ServiceModel.ReliableSession>, Ve<xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğelerinin doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6f04-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="e6f04-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e6f04-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e6f04-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e6f04-104">\<bindings></span></span>  
<span data-ttu-id="e6f04-105">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6f04-105">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f04-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6f04-106">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
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
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6f04-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f04-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e6f04-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6f04-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6f04-109">Attributes</span></span>  
  
|<span data-ttu-id="e6f04-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6f04-110">Attribute</span></span>|<span data-ttu-id="e6f04-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f04-111">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="e6f04-112">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="e6f04-113">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e6f04-114">Bu özelliği, tanımlama bilgilerini kullanan ASP.NET Web Hizmetleri (ASMX) ile etkileşim kurarken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6f04-114">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="e6f04-115">Bu, sunucunun döndürdüğü tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6f04-115">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="e6f04-116">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-116">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="e6f04-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-117">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="e6f04-118">Bir <xref:System.TimeSpan> Close işleminin tamamlanacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-118">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="e6f04-119">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f04-120">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-120">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="e6f04-121">Tekdüzen Kaynak tanımlayıcılarını (URI) ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-121">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="e6f04-122">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="e6f04-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="e6f04-123">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="e6f04-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="e6f04-124">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6f04-124">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e6f04-125">Varsayılan değer 524.288 bayttır (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="e6f04-125">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="e6f04-126">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e6f04-127">Arabellekler için çöp toplama gibi, her kullanıldıkları sırada arabellekleri oluşturma ve yok etme işlemleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-127">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="e6f04-128">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6f04-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="e6f04-129">Bu, arabellekleri oluşturma ve yok etme içindeki ek yükü önler.</span><span class="sxs-lookup"><span data-stu-id="e6f04-129">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="e6f04-130">Bu bağlama ile yapılandırılan bir kanalın alabileceği üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6f04-130">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="e6f04-131">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-131">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="e6f04-132">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6f04-132">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e6f04-133">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-133">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="e6f04-134">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6f04-134">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="e6f04-135">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e6f04-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6f04-136">-   `Text`: Bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6f04-136">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="e6f04-137">-   `Mtom`: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6f04-137">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="e6f04-138">Varsayılan, `Text` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-138">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="e6f04-139">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="e6f04-139">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="e6f04-140">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="e6f04-140">The configuration name of the binding.</span></span> <span data-ttu-id="e6f04-141">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-141">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e6f04-142">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e6f04-142">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e6f04-143">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="e6f04-143">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e6f04-144">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e6f04-145">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f04-146">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-146">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="e6f04-147">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="e6f04-147">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="e6f04-148">`useSystemWebProxy` İse`true`,buayar olmalıdır. `null`</span><span class="sxs-lookup"><span data-stu-id="e6f04-148">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="e6f04-149">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-149">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e6f04-150">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e6f04-151">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f04-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-152">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e6f04-153">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e6f04-154">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e6f04-155">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-155">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="e6f04-156">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-156">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="e6f04-157">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e6f04-157">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e6f04-158">-   `UnicodeFffeTextEncoding`: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="e6f04-158">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="e6f04-159">-   `Utf16TextEncoding`: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="e6f04-159">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="e6f04-160">-   `Utf8TextEncoding`: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="e6f04-160">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="e6f04-161">Varsayılan, `Utf8TextEncoding` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-161">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="e6f04-162">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e6f04-162">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="e6f04-163">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-163">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="e6f04-164">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-164">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="e6f04-165">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e6f04-165">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="e6f04-166">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6f04-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f04-167">Child Elements</span></span>  
  
|<span data-ttu-id="e6f04-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6f04-168">Element</span></span>|<span data-ttu-id="e6f04-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f04-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6f04-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e6f04-170">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="e6f04-171">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6f04-171">Defines the security settings for the binding.</span></span> <span data-ttu-id="e6f04-172">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e6f04-172">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="e6f04-173">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e6f04-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e6f04-174">Bu bağlama ile yapılandırılan bitiş noktaları tarafından kullanılabilen SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6f04-174">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="e6f04-175">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e6f04-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="e6f04-176">[\<Reliableoturum >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e6f04-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="e6f04-177">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6f04-178">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6f04-178">Parent Elements</span></span>  
  
|<span data-ttu-id="e6f04-179">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6f04-179">Element</span></span>|<span data-ttu-id="e6f04-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f04-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6f04-181">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e6f04-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e6f04-182">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e6f04-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f04-183">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6f04-183">Remarks</span></span>  
 <span data-ttu-id="e6f04-184">, `WS2007HttpBinding` ' A `WSHttpBinding` benzer bir sistem tarafından sağlanmış bir bağlama ekler, ancak bu, bir kuruluştan, reliableoturum, güvenlik ve TransactionFlow protokollerinin yapılandırılmış bilgi standartları (Oasa) standart sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6f04-184">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="e6f04-185">Bu bağlama kullanılırken nesne modelinde veya varsayılan ayarlarda değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e6f04-185">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f04-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6f04-186">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
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
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e6f04-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f04-187">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="e6f04-188">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e6f04-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6f04-189">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e6f04-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e6f04-190">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e6f04-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e6f04-191">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e6f04-191">\<binding></span></span>](../../../misc/binding.md)
