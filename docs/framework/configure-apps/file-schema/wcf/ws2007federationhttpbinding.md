---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe9ab2e19706a5d295b5916aeb818621d1132c11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558777"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="186a3-101">' Dan türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="186a3-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="186a3-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="186a3-102">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
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
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="186a3-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="186a3-103">Attributes and Elements</span></span>

<span data-ttu-id="186a3-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="186a3-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="186a3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="186a3-105">Attributes</span></span>

|<span data-ttu-id="186a3-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="186a3-106">Attribute</span></span>|<span data-ttu-id="186a3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="186a3-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="186a3-108">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="186a3-109">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="186a3-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="186a3-110"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="186a3-111">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="186a3-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="186a3-112">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="186a3-113">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="186a3-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="186a3-114">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="186a3-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="186a3-115">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="186a3-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="186a3-116">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="186a3-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="186a3-117">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="186a3-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="186a3-118">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="186a3-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="186a3-119">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="186a3-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="186a3-120">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="186a3-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="186a3-121">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="186a3-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="186a3-122">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="186a3-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="186a3-123">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="186a3-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="186a3-124">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="186a3-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="186a3-125">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="186a3-126">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="186a3-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="186a3-127">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="186a3-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="186a3-128">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="186a3-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="186a3-129">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="186a3-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="186a3-130">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="186a3-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="186a3-131">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="186a3-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="186a3-132">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="186a3-132">The configuration name of the binding.</span></span> <span data-ttu-id="186a3-133">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="186a3-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="186a3-134">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="186a3-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="186a3-135">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="186a3-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="186a3-136">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="186a3-137">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="186a3-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="186a3-138">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="186a3-139">Gizlilik bildiriminin bulunduğu URI.</span><span class="sxs-lookup"><span data-stu-id="186a3-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="186a3-140">Geçerli gizlilik bildiriminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="186a3-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="186a3-141">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="186a3-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="186a3-142">`useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="186a3-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="186a3-143">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="186a3-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="186a3-144"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="186a3-145">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="186a3-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="186a3-146">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="186a3-147"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="186a3-148">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="186a3-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="186a3-149">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="186a3-150">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="186a3-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="186a3-151">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="186a3-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="186a3-152">-Bigendianunıcode: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="186a3-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="186a3-153">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="186a3-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="186a3-154">-UTF8:8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="186a3-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="186a3-155">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="186a3-155">The default is UTF8.</span></span> <span data-ttu-id="186a3-156">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="186a3-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="186a3-157">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="186a3-158">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="186a3-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="186a3-159">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="186a3-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="186a3-160">Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="186a3-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="186a3-161">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="186a3-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="186a3-162">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="186a3-162">Child Elements</span></span>

|<span data-ttu-id="186a3-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="186a3-163">Element</span></span>|<span data-ttu-id="186a3-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="186a3-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="186a3-165">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="186a3-165">Defines the security settings for the message.</span></span> <span data-ttu-id="186a3-166">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="186a3-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="186a3-167">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="186a3-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="186a3-168">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="186a3-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="186a3-169">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="186a3-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="186a3-170">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="186a3-170">Parent Elements</span></span>

|<span data-ttu-id="186a3-171">Öğe</span><span class="sxs-lookup"><span data-stu-id="186a3-171">Element</span></span>|<span data-ttu-id="186a3-172">Açıklama</span><span class="sxs-lookup"><span data-stu-id="186a3-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="186a3-173">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="186a3-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="186a3-174">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="186a3-174">Remarks</span></span>

<span data-ttu-id="186a3-175">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla kurumda kimlik paylaşma veya etki alanına güven verme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="186a3-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="186a3-176">Kimlik gösterimini bir güven etki alanından diğerine eşlemek için WS-Trust protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="186a3-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="186a3-177">Federasyon HTTP bağlama, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="186a3-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="186a3-178">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="186a3-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="186a3-179">Daha fazla bilgi için bkz. [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="186a3-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="186a3-180">Örnek</span><span class="sxs-lookup"><span data-stu-id="186a3-180">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
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

## <a name="see-also"></a><span data-ttu-id="186a3-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="186a3-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="186a3-182">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="186a3-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="186a3-183">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="186a3-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="186a3-184">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="186a3-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
