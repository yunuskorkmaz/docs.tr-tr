---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 8ed8f62f9415ed556a61ca53f27442a9355d8d7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698856"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="37272-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="37272-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="37272-102">WS-Federation destekleyen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37272-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="37272-103">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="37272-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="37272-104">\<bağlamaları > \\</span><span class="sxs-lookup"><span data-stu-id="37272-104">\<bindings>\\</span></span>
<span data-ttu-id="37272-105">wsFederationBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="37272-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="37272-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37272-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="37272-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37272-107">Attributes and Elements</span></span>

<span data-ttu-id="37272-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37272-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="37272-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37272-109">Attributes</span></span>

|<span data-ttu-id="37272-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37272-110">Attribute</span></span>|<span data-ttu-id="37272-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37272-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="37272-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="37272-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="37272-113">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="37272-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="37272-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="37272-114">The default is `false`.</span></span>|
|<span data-ttu-id="37272-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="37272-115">closeTimeout</span></span>|<span data-ttu-id="37272-116">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="37272-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="37272-117">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="37272-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="37272-118">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="37272-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="37272-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="37272-119">hostnameComparisonMode</span></span>|<span data-ttu-id="37272-120">URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="37272-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="37272-121">Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37272-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="37272-122">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, ana bilgisayar adı eşleşme yok sayar.</span><span class="sxs-lookup"><span data-stu-id="37272-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="37272-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="37272-123">maxBufferPoolSize</span></span>|<span data-ttu-id="37272-124">Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="37272-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="37272-125">524.288 bayt (512 \* 1024) varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37272-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="37272-126">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="37272-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="37272-127">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="37272-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="37272-128">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="37272-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="37272-129">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="37272-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="37272-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="37272-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="37272-131">Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="37272-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="37272-132">Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız.</span><span class="sxs-lookup"><span data-stu-id="37272-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="37272-133">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37272-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="37272-134">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37272-134">The default is 65536.</span></span>|
|<span data-ttu-id="37272-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="37272-135">messageEncoding</span></span>|<span data-ttu-id="37272-136">İletisini kodlamak için kullanılan kodlayıcıya tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37272-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="37272-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37272-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="37272-138">-Metni: Bir metin ileti Kodlayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="37272-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="37272-139">-Mtom: İleti Aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="37272-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="37272-140">Metin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37272-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="37272-141">Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="37272-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="37272-142">name</span><span class="sxs-lookup"><span data-stu-id="37272-142">name</span></span>|<span data-ttu-id="37272-143">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="37272-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="37272-144">Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37272-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="37272-145">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="37272-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="37272-146">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="37272-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="37272-147">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="37272-147">openTimeout</span></span>|<span data-ttu-id="37272-148">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="37272-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="37272-149">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="37272-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="37272-150">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="37272-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="37272-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="37272-151">privacyNoticeAt</span></span>|<span data-ttu-id="37272-152">Gizlilik bildirimini bulunduğu bir URI öğesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="37272-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="37272-153">PrivacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="37272-153">privacyNoticeVersion</span></span>|<span data-ttu-id="37272-154">Geçerli gizlilik bildirimini sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="37272-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="37272-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="37272-155">proxyAddress</span></span>|<span data-ttu-id="37272-156">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="37272-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="37272-157">Varsa `useDefaultWebProxy` olduğu `true`, bu ayar olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="37272-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="37272-158">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="37272-158">The default is `null`.</span></span>|
|<span data-ttu-id="37272-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="37272-159">receiveTimeout</span></span>|<span data-ttu-id="37272-160">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="37272-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="37272-161">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="37272-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="37272-162">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="37272-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="37272-163">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="37272-163">sendTimeout</span></span>|<span data-ttu-id="37272-164">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="37272-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="37272-165">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="37272-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="37272-166">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="37272-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="37272-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="37272-167">textEncoding</span></span>|<span data-ttu-id="37272-168">İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="37272-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="37272-169">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="37272-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="37272-170">-   BigEndianUnicode: Unicode kodlama BigEndian.</span><span class="sxs-lookup"><span data-stu-id="37272-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="37272-171">-Unicode: 16-bit kodlaması.</span><span class="sxs-lookup"><span data-stu-id="37272-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="37272-172">-   UTF8: 8-bit kodlama</span><span class="sxs-lookup"><span data-stu-id="37272-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="37272-173">UTF8 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="37272-173">The default is UTF8.</span></span> <span data-ttu-id="37272-174">Bu öznitelik türünde <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="37272-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="37272-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="37272-175">transactionFlow</span></span>|<span data-ttu-id="37272-176">WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="37272-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="37272-177">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="37272-177">The default is `false`.</span></span>|
|<span data-ttu-id="37272-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="37272-178">useDefaultWebProxy</span></span>|<span data-ttu-id="37272-179">Sistemin otomatik yapılandırılan HTTP Ara sunucusu kullanılıp kullanılmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="37272-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="37272-180">Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlı değil) Bu öznitelik ise `true`.</span><span class="sxs-lookup"><span data-stu-id="37272-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="37272-181">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="37272-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="37272-182">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37272-182">Child Elements</span></span>

|<span data-ttu-id="37272-183">Öğe</span><span class="sxs-lookup"><span data-stu-id="37272-183">Element</span></span>|<span data-ttu-id="37272-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37272-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37272-185">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="37272-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="37272-186">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37272-186">Defines the security settings for the message.</span></span> <span data-ttu-id="37272-187">Bu öğe türünde <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="37272-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="37272-188">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37272-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="37272-189">Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37272-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="37272-190">Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="37272-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="37272-191">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="37272-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="37272-192">Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37272-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37272-193">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37272-193">Parent Elements</span></span>

|<span data-ttu-id="37272-194">Öğe</span><span class="sxs-lookup"><span data-stu-id="37272-194">Element</span></span>|<span data-ttu-id="37272-195">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37272-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37272-196">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="37272-196">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="37272-197">Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="37272-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37272-198">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37272-198">Remarks</span></span>

<span data-ttu-id="37272-199">Federasyon kimlikleri kimlik doğrulaması ve yetkilendirme için birden çok sistemleri arasında paylaşmak için yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="37272-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="37272-200">Bu kimlik, kullanıcılar veya makinelerin başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="37272-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="37272-201">Karma mod güvenliği yanı sıra SOAP Güvenliği Federasyon HTTP destekler ancak yalnızca Aktarım güvenliği kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="37272-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="37272-202">Bu bağlama için WS-Federation protokolü Windows Communication Foundation (WCF) desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="37272-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="37272-203">Bu bağlama ile yapılandırılan hizmetler, HTTP aktarımı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="37272-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="37272-204">Bağlamaları bağlama öğelerinin yığınını oluşur.</span><span class="sxs-lookup"><span data-stu-id="37272-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="37272-205">Yığın öğeleri bağlama</span><span class="sxs-lookup"><span data-stu-id="37272-205">The stack of binding elements in</span></span>

<span data-ttu-id="37272-206">`wsFederationHttpBinding` bulunan aynı `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="37272-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="37272-207">zaman [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) varsayılan değerine ayarlanır <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="37272-207">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="37272-208">`wsFederationHttpBinding` İleti güvenlik ayarlarının ayrıntılarını kontrol [ \<ileti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="37272-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="37272-209">Unutmayın [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) öğesi bağlama oluşturulduktan sonra yalnızca bağlama tarafından kullanılan güvenlik değiştirilemez olarak get erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="37272-209">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="37272-210">`wsFederationHttpBinding` Gizlilik bildirimini bulunduğu URI almak ve ayarlamak için bir privacyNoticeAt özniteliği de sağlar.</span><span class="sxs-lookup"><span data-stu-id="37272-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="37272-211">İlke güvende tutmanın, Federasyon senaryolarında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="37272-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="37272-212">İlke kötü amaçlı kullanıcılara karşı korumak için güvenlik, HTTPS gibi biçimi kullanmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="37272-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="37272-213">Bu bağlama kullanarak Federasyon senaryolarında hizmet ilkesi potansiyel olarak verilen (SAML) belirteç, belirteçte yerleştirin vb. için talep türünü şifrelemek için kullanılacak anahtarı gibi önemli bilgiler vardır.</span><span class="sxs-lookup"><span data-stu-id="37272-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="37272-214">Bu ilke değiştirilmiş, bir saldırganın başka oynama, bilgi ifşası ve diğer kötü amaçlı davranışları için önde gelen verilen belirteç anahtarı keşfedin.</span><span class="sxs-lookup"><span data-stu-id="37272-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="37272-215">Bunu önlemek için ilke (HTTPS kullanan güvenli bir şekilde örneğin) hizmetinden alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37272-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="37272-216">Bu bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="37272-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="37272-217">Örnek</span><span class="sxs-lookup"><span data-stu-id="37272-217">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="37272-218">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37272-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="37272-219">Nasıl yapılır: WSFederationHttpBinding oluşturma</span><span class="sxs-lookup"><span data-stu-id="37272-219">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="37272-220">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="37272-220">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="37272-221">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="37272-221">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="37272-222">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="37272-222">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="37272-223">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="37272-223">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
