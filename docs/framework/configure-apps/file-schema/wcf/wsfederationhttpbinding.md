---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 3c4edc17fd669fbe23ec38ff26a61e867c04c561
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915075"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="0e966-101">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0e966-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="0e966-102">WS-Federation destekleyen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="0e966-103">\<sistemin. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="0e966-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="0e966-104">\<bağlamalar > </span><span class="sxs-lookup"><span data-stu-id="0e966-104">\<bindings></span></span>\
<span data-ttu-id="0e966-105">wsFederationBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="0e966-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="0e966-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e966-106">Syntax</span></span>

```xml
<wsFederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
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
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e966-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e966-107">Attributes and Elements</span></span>

<span data-ttu-id="0e966-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e966-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e966-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e966-109">Attributes</span></span>

|<span data-ttu-id="0e966-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e966-110">Attribute</span></span>|<span data-ttu-id="0e966-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e966-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0e966-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="0e966-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="0e966-113">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0e966-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="0e966-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e966-114">The default is `false`.</span></span>|
|<span data-ttu-id="0e966-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="0e966-115">closeTimeout</span></span>|<span data-ttu-id="0e966-116">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0e966-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0e966-117">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e966-118">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0e966-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="0e966-119">hostnameComparisonMode</span></span>|<span data-ttu-id="0e966-120">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e966-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="0e966-121">Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="0e966-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="0e966-122">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="0e966-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="0e966-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0e966-123">maxBufferPoolSize</span></span>|<span data-ttu-id="0e966-124">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0e966-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="0e966-125">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="0e966-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="0e966-126">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e966-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="0e966-127">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="0e966-128">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e966-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="0e966-129">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="0e966-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="0e966-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0e966-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="0e966-131">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0e966-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="0e966-132">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="0e966-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="0e966-133">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e966-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="0e966-134">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-134">The default is 65536.</span></span>|
|<span data-ttu-id="0e966-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="0e966-135">messageEncoding</span></span>|<span data-ttu-id="0e966-136">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="0e966-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0e966-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e966-138">Metinleri Bir SMS mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e966-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="0e966-139">MTOM Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e966-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="0e966-140">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="0e966-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="0e966-141">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="0e966-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="0e966-142">name</span><span class="sxs-lookup"><span data-stu-id="0e966-142">name</span></span>|<span data-ttu-id="0e966-143">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0e966-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0e966-144">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0e966-145">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0e966-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0e966-146">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="0e966-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="0e966-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="0e966-147">openTimeout</span></span>|<span data-ttu-id="0e966-148">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0e966-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0e966-149">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e966-150">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0e966-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="0e966-151">privacyNoticeAt</span></span>|<span data-ttu-id="0e966-152">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0e966-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="0e966-153">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="0e966-153">privacyNoticeVersion</span></span>|<span data-ttu-id="0e966-154">Geçerli gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0e966-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="0e966-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="0e966-155">proxyAddress</span></span>|<span data-ttu-id="0e966-156">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="0e966-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="0e966-157">`useDefaultWebProxy` İse`true`,buayar olmalıdır. `null`</span><span class="sxs-lookup"><span data-stu-id="0e966-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="0e966-158">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e966-158">The default is `null`.</span></span>|
|<span data-ttu-id="0e966-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="0e966-159">receiveTimeout</span></span>|<span data-ttu-id="0e966-160">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0e966-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0e966-161">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e966-162">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="0e966-163">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="0e966-163">sendTimeout</span></span>|<span data-ttu-id="0e966-164">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0e966-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0e966-165">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0e966-166">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="0e966-167">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="0e966-167">textEncoding</span></span>|<span data-ttu-id="0e966-168">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="0e966-169">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0e966-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e966-170">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="0e966-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="0e966-171">Kodlamaları 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="0e966-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="0e966-172">UTF8 8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="0e966-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="0e966-173">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e966-173">The default is UTF8.</span></span> <span data-ttu-id="0e966-174">Bu öznitelik türü <xref:System.Text.Encoding>..</span><span class="sxs-lookup"><span data-stu-id="0e966-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="0e966-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="0e966-175">transactionFlow</span></span>|<span data-ttu-id="0e966-176">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0e966-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="0e966-177">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e966-177">The default is `false`.</span></span>|
|<span data-ttu-id="0e966-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="0e966-178">useDefaultWebProxy</span></span>|<span data-ttu-id="0e966-179">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="0e966-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="0e966-180">Bu öznitelik ise `true`, ara `null` sunucu adresi (ayarlı değil) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="0e966-181">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e966-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0e966-182">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e966-182">Child Elements</span></span>

|<span data-ttu-id="0e966-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e966-183">Element</span></span>|<span data-ttu-id="0e966-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e966-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e966-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0e966-185">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="0e966-186">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-186">Defines the security settings for the message.</span></span> <span data-ttu-id="0e966-187">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0e966-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="0e966-188">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0e966-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="0e966-189">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="0e966-190">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="0e966-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="0e966-191">[\<Reliableoturum >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0e966-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="0e966-192">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e966-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0e966-193">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e966-193">Parent Elements</span></span>

|<span data-ttu-id="0e966-194">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e966-194">Element</span></span>|<span data-ttu-id="0e966-195">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e966-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e966-196">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0e966-196">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0e966-197">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0e966-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e966-198">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e966-198">Remarks</span></span>

<span data-ttu-id="0e966-199">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla sistem genelinde kimlik paylaşma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="0e966-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="0e966-200">Bu kimlikler, kullanıcılara veya makinelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="0e966-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="0e966-201">Federasyon HTTP, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini kullanarak özel olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0e966-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="0e966-202">Bu bağlama WS-Federation protokolü için Windows Communication Foundation (WCF) desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="0e966-203">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e966-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="0e966-204">Bağlamalar bağlama öğelerinden oluşan bir yığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="0e966-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="0e966-205">İçindeki bağlama öğelerinin yığını</span><span class="sxs-lookup"><span data-stu-id="0e966-205">The stack of binding elements in</span></span>

<span data-ttu-id="0e966-206">`wsFederationHttpBinding`, içinde bulunan ile aynıdır`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="0e966-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="0e966-207">Güvenlik > varsayılan değerine <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>ayarlandığında. [ \<](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0e966-207">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="0e966-208">İleti > ileti güvenlik `wsFederationHttpBinding` [ \<](message-element-of-wsfederationhttpbinding.md)ayarlarının ayrıntılarını denetler.</span><span class="sxs-lookup"><span data-stu-id="0e966-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="0e966-209">Güvenlik > öğesinin yalnızca bağlama tarafından kullanılan güvenlik, bağlama oluşturulduktan sonra değiştirilemez olarak erişim sağladığını unutmayın. [ \<](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0e966-209">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="0e966-210">Ayrıca `wsFederationHttpBinding` , gizlilik bildiriminin bulunduğu URI 'yi ayarlamak ve almak için bir privacyNoticeAt özniteliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e966-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="0e966-211">İlkenin güvenli tutulması, Federasyon senaryolarında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0e966-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="0e966-212">Bu öneri, ilkeyi kötü amaçlı kullanıcılardan korumak için HTTPS gibi bir güvenlik biçimi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e966-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="0e966-213">Bu bağlamayı kullanan Federasyon senaryolarında, hizmet ilkesi potansiyel olarak, verilen (SAML) belirtecini şifrelemek için kullanılan anahtar, belirtece yerleştirilecek talepler türü ve benzeri önemli bilgilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0e966-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="0e966-214">Bu ilke ile oynanabilir bir saldırgan, verilen belirtecin anahtarını daha fazla değişiklik, bilgi açığa çıkması ve diğer kötü amaçlı davranışa göre bulabilir.</span><span class="sxs-lookup"><span data-stu-id="0e966-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="0e966-215">Bunu önlemeye yardımcı olmak için, ilkenin hizmetten güvenli bir şekilde (örneğin, HTTPS kullanılarak) alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e966-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="0e966-216">Bu bağlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0e966-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e966-217">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e966-217">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0e966-218">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e966-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="0e966-219">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e966-219">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="0e966-220">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0e966-220">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0e966-221">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0e966-221">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0e966-222">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e966-222">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0e966-223">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0e966-223">\<binding></span></span>](../../../misc/binding.md)
