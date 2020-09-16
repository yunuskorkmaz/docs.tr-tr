---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 102e220ad01410568a18ce4ea6fac06ca8c15230
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558738"
---
# \<ws2007HttpBinding>
<span data-ttu-id="44b5a-101"><xref:System.ServiceModel.WSHttpBinding.Security%2A>,, <xref:System.ServiceModel.ReliableSession> Ve bağlama öğelerinin doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-101">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="44b5a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="44b5a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44b5a-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44b5a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="44b5a-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44b5a-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44b5a-105">Attributes</span></span>  
  
|<span data-ttu-id="44b5a-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44b5a-106">Attribute</span></span>|<span data-ttu-id="44b5a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44b5a-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="44b5a-108">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-108">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="44b5a-109">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="44b5a-110">Bu özelliği, tanımlama bilgilerini kullanan ASP.NET Web Hizmetleri (ASMX) ile etkileşim kurarken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b5a-110">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="44b5a-111">Bu, sunucunun döndürdüğü tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="44b5a-111">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="44b5a-112">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-112">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="44b5a-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-113">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="44b5a-114"><xref:System.TimeSpan>Bir Close işleminin tamamlanacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-114">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="44b5a-115">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44b5a-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="44b5a-117">Tekdüzen Kaynak tanımlayıcılarını (URI) ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-117">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="44b5a-118">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="44b5a-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="44b5a-119">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="44b5a-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="44b5a-120">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="44b5a-120">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="44b5a-121">Varsayılan değer 524.288 bayttır (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="44b5a-121">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="44b5a-122">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="44b5a-123">Arabellekler için çöp toplama gibi, her kullanıldıkları sırada arabellekleri oluşturma ve yok etme işlemleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-123">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="44b5a-124">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44b5a-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="44b5a-125">Bu, arabellekleri oluşturma ve yok etme içindeki ek yükü önler.</span><span class="sxs-lookup"><span data-stu-id="44b5a-125">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="44b5a-126">Bu bağlama ile yapılandırılan bir kanalın alabileceği üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="44b5a-126">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="44b5a-127">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-127">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="44b5a-128">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44b5a-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="44b5a-129">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-129">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="44b5a-130">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44b5a-130">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="44b5a-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44b5a-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="44b5a-132">-   `Text`: Bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="44b5a-132">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="44b5a-133">-   `Mtom`: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="44b5a-133">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="44b5a-134">Varsayılan değer: `Text`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-134">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="44b5a-135">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-135">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="44b5a-136">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="44b5a-136">The configuration name of the binding.</span></span> <span data-ttu-id="44b5a-137">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-137">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="44b5a-138">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-138">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="44b5a-139">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="44b5a-139">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="44b5a-140">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="44b5a-141">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44b5a-142">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-142">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="44b5a-143">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="44b5a-143">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="44b5a-144">`useSystemWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="44b5a-144">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="44b5a-145">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-145">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="44b5a-146"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="44b5a-147">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44b5a-148">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-148">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="44b5a-149"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="44b5a-150">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="44b5a-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-151">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="44b5a-152">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-152">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="44b5a-153">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44b5a-153">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="44b5a-154">-   `UnicodeFffeTextEncoding`: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="44b5a-154">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="44b5a-155">-   `Utf16TextEncoding`: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="44b5a-155">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="44b5a-156">-   `Utf8TextEncoding`: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="44b5a-156">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="44b5a-157">Varsayılan değer: `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-157">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="44b5a-158">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-158">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="44b5a-159">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-159">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="44b5a-160">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-160">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="44b5a-161">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="44b5a-161">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="44b5a-162">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="44b5a-162">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44b5a-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44b5a-163">Child Elements</span></span>  
  
|<span data-ttu-id="44b5a-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="44b5a-164">Element</span></span>|<span data-ttu-id="44b5a-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44b5a-165">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="44b5a-166">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44b5a-166">Defines the security settings for the binding.</span></span> <span data-ttu-id="44b5a-167">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-167">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="44b5a-168">Bu bağlama ile yapılandırılan bitiş noktaları tarafından kullanılabilen SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44b5a-168">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="44b5a-169">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="44b5a-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="44b5a-170">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44b5a-171">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44b5a-171">Parent Elements</span></span>  
  
|<span data-ttu-id="44b5a-172">Öğe</span><span class="sxs-lookup"><span data-stu-id="44b5a-172">Element</span></span>|<span data-ttu-id="44b5a-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44b5a-173">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="44b5a-174">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="44b5a-174">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44b5a-175">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44b5a-175">Remarks</span></span>  
 <span data-ttu-id="44b5a-176">, `WS2007HttpBinding` ' A benzer bir sistem tarafından sağlanmış bir bağlama ekler, ancak bu, bir `WSHttpBinding` kuruluştan, Reliableoturum, güvenlik ve TransactionFlow protokollerinin yapılandırılmış bilgi standartları (Oasa) standart sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44b5a-176">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="44b5a-177">Bu bağlama kullanılırken nesne modelinde veya varsayılan ayarlarda değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="44b5a-177">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b5a-178">Örnek</span><span class="sxs-lookup"><span data-stu-id="44b5a-178">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44b5a-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44b5a-179">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="44b5a-180">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="44b5a-180">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="44b5a-181">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="44b5a-181">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="44b5a-182">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="44b5a-182">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
