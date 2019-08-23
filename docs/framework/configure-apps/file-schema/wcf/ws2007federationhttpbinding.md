---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe952dfe9ce51e23d1ba46975026799dfe8b5b39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915271"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="62c3b-101">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="62c3b-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="62c3b-102">[ \<WSFederationHttpBinding >](wsfederationhttpbinding.md) türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="62c3b-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a><span data-ttu-id="62c3b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62c3b-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="62c3b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c3b-104">Attributes and Elements</span></span>

<span data-ttu-id="62c3b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="62c3b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62c3b-106">Attributes</span></span>

|<span data-ttu-id="62c3b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="62c3b-107">Attribute</span></span>|<span data-ttu-id="62c3b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62c3b-108">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="62c3b-109">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-109">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="62c3b-110">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-110">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="62c3b-111">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-111">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="62c3b-112">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-112">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62c3b-113">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-113">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="62c3b-114">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="62c3b-115">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="62c3b-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="62c3b-116">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="62c3b-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="62c3b-117">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="62c3b-117">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="62c3b-118">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="62c3b-118">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="62c3b-119">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-119">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="62c3b-120">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-120">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="62c3b-121">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62c3b-121">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="62c3b-122">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="62c3b-122">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="62c3b-123">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="62c3b-123">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="62c3b-124">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-124">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="62c3b-125">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62c3b-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="62c3b-126">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-126">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="62c3b-127">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62c3b-127">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="62c3b-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="62c3b-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62c3b-129">Metinleri Bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="62c3b-129">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="62c3b-130">MTOM Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="62c3b-130">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="62c3b-131">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-131">The default is Text.</span></span><br /><br /> <span data-ttu-id="62c3b-132">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="62c3b-132">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="62c3b-133">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="62c3b-133">The configuration name of the binding.</span></span> <span data-ttu-id="62c3b-134">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="62c3b-135">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="62c3b-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="62c3b-136">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="62c3b-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="62c3b-137">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="62c3b-138">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62c3b-139">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-139">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="62c3b-140">Gizlilik bildiriminin bulunduğu URI.</span><span class="sxs-lookup"><span data-stu-id="62c3b-140">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="62c3b-141">Geçerli gizlilik bildiriminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="62c3b-141">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="62c3b-142">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="62c3b-142">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="62c3b-143">`useDefaultWebProxy` İse`true`,buayar olmalıdır. `null`</span><span class="sxs-lookup"><span data-stu-id="62c3b-143">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="62c3b-144">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-144">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="62c3b-145">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="62c3b-146">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62c3b-147">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-147">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="62c3b-148">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="62c3b-149">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62c3b-150">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-150">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="62c3b-151">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="62c3b-151">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="62c3b-152">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="62c3b-152">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62c3b-153">-Bigendianunıcode: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="62c3b-153">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="62c3b-154">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="62c3b-154">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="62c3b-155">UTF8 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="62c3b-155">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="62c3b-156">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-156">The default is UTF8.</span></span> <span data-ttu-id="62c3b-157">Bu öznitelik türü <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="62c3b-157">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="62c3b-158">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-158">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="62c3b-159">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-159">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="62c3b-160">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62c3b-160">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="62c3b-161">Bu öznitelik ise `true`, ara `null` sunucu adresi (ayarlı değil) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-161">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="62c3b-162">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-162">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="62c3b-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c3b-163">Child Elements</span></span>

|<span data-ttu-id="62c3b-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="62c3b-164">Element</span></span>|<span data-ttu-id="62c3b-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62c3b-165">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62c3b-166">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="62c3b-166">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="62c3b-167">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62c3b-167">Defines the security settings for the message.</span></span> <span data-ttu-id="62c3b-168">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="62c3b-168">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="62c3b-169">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62c3b-169">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="62c3b-170">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62c3b-170">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="62c3b-171">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="62c3b-171">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="62c3b-172">[\<Reliableoturum >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="62c3b-172">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="62c3b-173">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-173">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62c3b-174">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="62c3b-174">Parent Elements</span></span>

|<span data-ttu-id="62c3b-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="62c3b-175">Element</span></span>|<span data-ttu-id="62c3b-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62c3b-176">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62c3b-177">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="62c3b-177">\<bindings></span></span>](bindings.md)|<span data-ttu-id="62c3b-178">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-178">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62c3b-179">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62c3b-179">Remarks</span></span>

<span data-ttu-id="62c3b-180">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla kurumda kimlik paylaşma veya etki alanına güven verme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-180">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="62c3b-181">Kimlik gösterimini bir güven etki alanından diğerine eşlemek için WS-Trust protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="62c3b-181">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="62c3b-182">Federasyon HTTP bağlama, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="62c3b-182">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="62c3b-183">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62c3b-183">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="62c3b-184">Daha fazla bilgi için bkz [ \<. WSFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="62c3b-184">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="62c3b-185">Örnek</span><span class="sxs-lookup"><span data-stu-id="62c3b-185">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62c3b-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62c3b-186">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="62c3b-187">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="62c3b-187">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="62c3b-188">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="62c3b-188">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62c3b-189">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="62c3b-189">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="62c3b-190">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="62c3b-190">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="62c3b-191">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="62c3b-191">\<binding></span></span>](../../../misc/binding.md)
