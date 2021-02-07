---
description: 'Hakkında daha fazla bilgi edinin: <ws2007FederationHttpBinding>'
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 90635805573e5bee64d8adf0f79de827733f178b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682195"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="b4794-102">' Dan türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b4794-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="b4794-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b4794-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b4794-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4794-104">Attributes and Elements</span></span>

<span data-ttu-id="b4794-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4794-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4794-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4794-106">Attributes</span></span>

|<span data-ttu-id="b4794-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b4794-107">Attribute</span></span>|<span data-ttu-id="b4794-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4794-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="b4794-109">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b4794-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="b4794-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="b4794-111"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b4794-112">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="b4794-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b4794-113">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="b4794-114">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4794-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b4794-115">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="b4794-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b4794-116">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="b4794-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="b4794-117">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="b4794-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b4794-118">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="b4794-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="b4794-119">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4794-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b4794-120">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4794-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="b4794-121">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4794-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="b4794-122">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="b4794-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="b4794-123">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="b4794-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b4794-124">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="b4794-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="b4794-125">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4794-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b4794-126">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="b4794-127">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4794-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b4794-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b4794-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b4794-129">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4794-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b4794-130">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4794-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b4794-131">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="b4794-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="b4794-132">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="b4794-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="b4794-133">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="b4794-133">The configuration name of the binding.</span></span> <span data-ttu-id="b4794-134">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4794-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b4794-135">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b4794-135">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b4794-136">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="b4794-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="b4794-137">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b4794-138">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="b4794-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b4794-139">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="b4794-140">Gizlilik bildiriminin bulunduğu URI.</span><span class="sxs-lookup"><span data-stu-id="b4794-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="b4794-141">Geçerli gizlilik bildiriminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="b4794-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="b4794-142">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="b4794-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b4794-143">`useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="b4794-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b4794-144">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="b4794-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="b4794-145"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b4794-146">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="b4794-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b4794-147">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="b4794-148"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b4794-149">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="b4794-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b4794-150">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="b4794-151">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b4794-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b4794-152">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b4794-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b4794-153">-Bigendianunıcode: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="b4794-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b4794-154">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="b4794-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b4794-155">-UTF8:8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="b4794-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b4794-156">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b4794-156">The default is UTF8.</span></span> <span data-ttu-id="b4794-157">Bu öznitelik türü <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="b4794-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="b4794-158">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b4794-159">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="b4794-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="b4794-160">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b4794-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b4794-161">Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="b4794-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="b4794-162">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="b4794-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b4794-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4794-163">Child Elements</span></span>

|<span data-ttu-id="b4794-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4794-164">Element</span></span>|<span data-ttu-id="b4794-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4794-165">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="b4794-166">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4794-166">Defines the security settings for the message.</span></span> <span data-ttu-id="b4794-167">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="b4794-167">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="b4794-168">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4794-168">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b4794-169">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="b4794-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="b4794-170">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4794-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4794-171">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4794-171">Parent Elements</span></span>

|<span data-ttu-id="b4794-172">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4794-172">Element</span></span>|<span data-ttu-id="b4794-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4794-173">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="b4794-174">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="b4794-174">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4794-175">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4794-175">Remarks</span></span>

<span data-ttu-id="b4794-176">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla kurumda kimlik paylaşma veya etki alanına güven verme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="b4794-176">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="b4794-177">Kimlik gösterimini bir güven etki alanından diğerine eşlemek için WS-Trust protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4794-177">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="b4794-178">Federasyon HTTP bağlama, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b4794-178">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="b4794-179">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4794-179">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="b4794-180">Daha fazla bilgi için bkz. [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b4794-180">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4794-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4794-181">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4794-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4794-182">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="b4794-183">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b4794-183">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b4794-184">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b4794-184">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b4794-185">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b4794-185">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
