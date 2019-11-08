---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 2f8cff87280f08af0c426b7a726949b9a9c40197
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732520"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="7136d-101">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="7136d-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="7136d-102"><xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğelerinin doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7136d-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="7136d-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7136d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7136d-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7136d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7136d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7136d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7136d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="7136d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7136d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7136d-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7136d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7136d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7136d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7136d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7136d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7136d-110">Attributes</span></span>  
  
|<span data-ttu-id="7136d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7136d-111">Attribute</span></span>|<span data-ttu-id="7136d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7136d-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="7136d-113">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7136d-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="7136d-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7136d-115">Bu özelliği, tanımlama bilgilerini kullanan ASP.NET Web Hizmetleri (ASMX) ile etkileşim kurarken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7136d-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="7136d-116">Bu, sunucunun döndürdüğü tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7136d-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="7136d-117">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7136d-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="7136d-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="7136d-119">Bir Close işleminin tamamlanacağı zaman aralığını belirten <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="7136d-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="7136d-120">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7136d-121">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7136d-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="7136d-122">Tekdüzen Kaynak tanımlayıcılarını (URI) ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7136d-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="7136d-123">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="7136d-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7136d-124">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="7136d-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7136d-125">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="7136d-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7136d-126">Varsayılan değer 524.288 bayttır (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="7136d-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="7136d-127">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="7136d-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7136d-128">Arabellekler için çöp toplama gibi, her kullanıldıkları sırada arabellekleri oluşturma ve yok etme işlemleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="7136d-129">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7136d-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="7136d-130">Bu, arabellekleri oluşturma ve yok etme içindeki ek yükü önler.</span><span class="sxs-lookup"><span data-stu-id="7136d-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7136d-131">Bu bağlama ile yapılandırılan bir kanalın alabileceği üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="7136d-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="7136d-132">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="7136d-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="7136d-133">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7136d-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7136d-134">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7136d-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="7136d-135">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7136d-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="7136d-136">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7136d-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7136d-137">-   `Text`: bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7136d-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="7136d-138">-   `Mtom`: bir Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="7136d-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="7136d-139">Varsayılan, `Text` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="7136d-140">Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="7136d-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="7136d-141">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="7136d-141">The configuration name of the binding.</span></span> <span data-ttu-id="7136d-142">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7136d-143">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7136d-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7136d-144">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="7136d-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7136d-145">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="7136d-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7136d-146">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7136d-147">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7136d-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="7136d-148">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="7136d-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="7136d-149">`useSystemWebProxy` `true`, bu ayar `null`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="7136d-150">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7136d-151">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="7136d-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7136d-152">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7136d-153">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7136d-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7136d-154">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="7136d-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7136d-155">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7136d-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7136d-156">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7136d-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="7136d-157">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7136d-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="7136d-158">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7136d-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7136d-159">-   `UnicodeFffeTextEncoding`: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="7136d-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="7136d-160">-   `Utf16TextEncoding`: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="7136d-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="7136d-161">-   `Utf8TextEncoding`: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="7136d-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="7136d-162">Varsayılan, `Utf8TextEncoding` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="7136d-163">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="7136d-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="7136d-164">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7136d-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7136d-165">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="7136d-166">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7136d-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="7136d-167">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7136d-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7136d-168">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7136d-168">Child Elements</span></span>  
  
|<span data-ttu-id="7136d-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="7136d-169">Element</span></span>|<span data-ttu-id="7136d-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7136d-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7136d-171">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7136d-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="7136d-172">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7136d-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="7136d-173">Bu öğe <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="7136d-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="7136d-174">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7136d-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="7136d-175">Bu bağlama ile yapılandırılan bitiş noktaları tarafından kullanılabilen SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7136d-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="7136d-176">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="7136d-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="7136d-177">[Reliableoturum > \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7136d-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="7136d-178">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7136d-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7136d-179">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7136d-179">Parent Elements</span></span>  
  
|<span data-ttu-id="7136d-180">Öğe</span><span class="sxs-lookup"><span data-stu-id="7136d-180">Element</span></span>|<span data-ttu-id="7136d-181">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7136d-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7136d-182">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="7136d-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="7136d-183">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7136d-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7136d-184">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7136d-184">Remarks</span></span>  
 <span data-ttu-id="7136d-185">`WS2007HttpBinding`, `WSHttpBinding` benzer bir sistem tarafından sağlanmış bağlama ekler ancak organizasyonu, Reliableoturum, güvenlik ve TransactionFlow protokollerinin yapılandırılmış bilgi standartları (OASA) standart sürümlerinin Ilerlediği için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7136d-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="7136d-186">Bu bağlama kullanılırken nesne modelinde veya varsayılan ayarlarda değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7136d-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7136d-187">Örnek</span><span class="sxs-lookup"><span data-stu-id="7136d-187">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7136d-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7136d-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="7136d-189">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7136d-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7136d-190">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7136d-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7136d-191">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7136d-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7136d-192">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="7136d-192">\<binding></span></span>](bindings.md)
