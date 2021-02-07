---
description: 'Hakkında daha fazla bilgi edinin: <ws2007HttpBinding>'
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 1a74fb604054a4215c89c2d772ee4f83e6416a08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682169"
---
# \<ws2007HttpBinding>

<span data-ttu-id="ff1ff-102"><xref:System.ServiceModel.WSHttpBinding.Security%2A>,, <xref:System.ServiceModel.ReliableSession> Ve bağlama öğelerinin doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="ff1ff-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff1ff-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff1ff-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff1ff-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ff1ff-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff1ff-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff1ff-106">Attributes</span></span>  
  
|<span data-ttu-id="ff1ff-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff1ff-107">Attribute</span></span>|<span data-ttu-id="ff1ff-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff1ff-108">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="ff1ff-109">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-109">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="ff1ff-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-110">The default is `false`.</span></span><br /><br /> <span data-ttu-id="ff1ff-111">Bu özelliği, tanımlama bilgilerini kullanan ASP.NET Web Hizmetleri (ASMX) ile etkileşim kurarken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-111">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="ff1ff-112">Bu, sunucunun döndürdüğü tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-112">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="ff1ff-113">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="ff1ff-114">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="ff1ff-115"><xref:System.TimeSpan>Bir Close işleminin tamamlanacağı zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-115">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="ff1ff-116">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff1ff-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-117">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="ff1ff-118">Tekdüzen Kaynak tanımlayıcılarını (URI) ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-118">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="ff1ff-119">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="ff1ff-120">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="ff1ff-121">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="ff1ff-122">Varsayılan değer 524.288 bayttır (512 × 1.024).</span><span class="sxs-lookup"><span data-stu-id="ff1ff-122">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="ff1ff-123">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="ff1ff-124">Arabellekler için çöp toplama gibi, her kullanıldıkları sırada arabellekleri oluşturma ve yok etme işlemleri pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-124">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="ff1ff-125">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="ff1ff-126">Bu, arabellekleri oluşturma ve yok etme içindeki ek yükü önler.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-126">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="ff1ff-127">Bu bağlama ile yapılandırılan bir kanalın alabileceği üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-127">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="ff1ff-128">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-128">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="ff1ff-129">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="ff1ff-130">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="ff1ff-131">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="ff1ff-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ff1ff-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ff1ff-133">-   `Text`: Bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-133">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="ff1ff-134">-   `Mtom`: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-134">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="ff1ff-135">Varsayılan değer: `Text`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-135">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="ff1ff-136">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="ff1ff-137">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-137">The configuration name of the binding.</span></span> <span data-ttu-id="ff1ff-138">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ff1ff-139">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-139">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ff1ff-140">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ff1ff-141">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ff1ff-142">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff1ff-143">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-143">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="ff1ff-144">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-144">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="ff1ff-145">`useSystemWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-145">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="ff1ff-146">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-146">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ff1ff-147"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ff1ff-148">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff1ff-149">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-149">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ff1ff-150"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ff1ff-151">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ff1ff-152">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-152">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="ff1ff-153">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-153">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="ff1ff-154">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ff1ff-154">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ff1ff-155">-   `UnicodeFffeTextEncoding`: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-155">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="ff1ff-156">-   `Utf16TextEncoding`: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-156">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="ff1ff-157">-   `Utf8TextEncoding`: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-157">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="ff1ff-158">Varsayılan değer: `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-158">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="ff1ff-159">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-159">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="ff1ff-160">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-160">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="ff1ff-161">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-161">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="ff1ff-162">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-162">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="ff1ff-163">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-163">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff1ff-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff1ff-164">Child Elements</span></span>  
  
|<span data-ttu-id="ff1ff-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff1ff-165">Element</span></span>|<span data-ttu-id="ff1ff-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff1ff-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="ff1ff-167">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="ff1ff-168">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-168">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="ff1ff-169">Bu bağlama ile yapılandırılan bitiş noktaları tarafından kullanılabilen SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-169">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="ff1ff-170">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="ff1ff-171">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-171">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff1ff-172">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff1ff-172">Parent Elements</span></span>  
  
|<span data-ttu-id="ff1ff-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff1ff-173">Element</span></span>|<span data-ttu-id="ff1ff-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff1ff-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="ff1ff-175">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff1ff-176">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff1ff-176">Remarks</span></span>  

 <span data-ttu-id="ff1ff-177">, `WS2007HttpBinding` ' A benzer bir sistem tarafından sağlanmış bir bağlama ekler, ancak bu, bir `WSHttpBinding` kuruluştan, Reliableoturum, güvenlik ve TransactionFlow protokollerinin yapılandırılmış bilgi standartları (Oasa) standart sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-177">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="ff1ff-178">Bu bağlama kullanılırken nesne modelinde veya varsayılan ayarlarda değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-178">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff1ff-179">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff1ff-179">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff1ff-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-180">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="ff1ff-181">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ff1ff-181">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ff1ff-182">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff1ff-182">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ff1ff-183">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ff1ff-183">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
