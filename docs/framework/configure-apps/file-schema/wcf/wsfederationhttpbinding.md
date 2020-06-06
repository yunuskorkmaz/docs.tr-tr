---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 0a77c791d55c6009cf59d5a4b15f3b2a63b7ccf9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140467"
---
# \<wsFederationHttpBinding>

<span data-ttu-id="02ac8-101">WS-Federation destekleyen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-101">Defines a binding that supports WS-Federation.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a><span data-ttu-id="02ac8-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02ac8-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="02ac8-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02ac8-103">Attributes and Elements</span></span>

<span data-ttu-id="02ac8-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="02ac8-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02ac8-105">Attributes</span></span>

|<span data-ttu-id="02ac8-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="02ac8-106">Attribute</span></span>|<span data-ttu-id="02ac8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02ac8-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="02ac8-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="02ac8-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="02ac8-109">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="02ac8-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="02ac8-110">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="02ac8-110">The default is `false`.</span></span>|
|<span data-ttu-id="02ac8-111">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="02ac8-111">closeTimeout</span></span>|<span data-ttu-id="02ac8-112"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="02ac8-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="02ac8-113">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02ac8-114">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-114">The default is 00:01:00.</span></span>|
|<span data-ttu-id="02ac8-115">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="02ac8-115">hostnameComparisonMode</span></span>|<span data-ttu-id="02ac8-116">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="02ac8-117">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="02ac8-117">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="02ac8-118">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="02ac8-118">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="02ac8-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="02ac8-119">maxBufferPoolSize</span></span>|<span data-ttu-id="02ac8-120">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="02ac8-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="02ac8-121">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="02ac8-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="02ac8-122">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="02ac8-123">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="02ac8-124">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02ac8-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="02ac8-125">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="02ac8-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="02ac8-126">Değerini</span><span class="sxs-lookup"><span data-stu-id="02ac8-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="02ac8-127">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="02ac8-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="02ac8-128">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="02ac8-129">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="02ac8-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="02ac8-130">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-130">The default is 65536.</span></span>|
|<span data-ttu-id="02ac8-131">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="02ac8-131">messageEncoding</span></span>|<span data-ttu-id="02ac8-132">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-132">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="02ac8-133">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="02ac8-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="02ac8-134">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="02ac8-134">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="02ac8-135">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="02ac8-135">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="02ac8-136">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-136">The default is Text.</span></span><br /><br /> <span data-ttu-id="02ac8-137">Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-137">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="02ac8-138">name</span><span class="sxs-lookup"><span data-stu-id="02ac8-138">name</span></span>|<span data-ttu-id="02ac8-139">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="02ac8-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="02ac8-140">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="02ac8-141">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="02ac8-142">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="02ac8-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="02ac8-143">openTimeout</span><span class="sxs-lookup"><span data-stu-id="02ac8-143">openTimeout</span></span>|<span data-ttu-id="02ac8-144">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="02ac8-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="02ac8-145">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02ac8-146">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-146">The default is 00:01:00.</span></span>|
|<span data-ttu-id="02ac8-147">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="02ac8-147">privacyNoticeAt</span></span>|<span data-ttu-id="02ac8-148">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="02ac8-148">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="02ac8-149">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="02ac8-149">privacyNoticeVersion</span></span>|<span data-ttu-id="02ac8-150">Geçerli gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="02ac8-150">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="02ac8-151">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="02ac8-151">proxyAddress</span></span>|<span data-ttu-id="02ac8-152">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="02ac8-152">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="02ac8-153">`useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="02ac8-153">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="02ac8-154">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="02ac8-154">The default is `null`.</span></span>|
|<span data-ttu-id="02ac8-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="02ac8-155">receiveTimeout</span></span>|<span data-ttu-id="02ac8-156"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="02ac8-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="02ac8-157">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02ac8-158">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-158">The default is 00:10:00.</span></span>|
|<span data-ttu-id="02ac8-159">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="02ac8-159">sendTimeout</span></span>|<span data-ttu-id="02ac8-160"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="02ac8-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="02ac8-161">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02ac8-162">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-162">The default is 00:01:00.</span></span>|
|<span data-ttu-id="02ac8-163">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="02ac8-163">textEncoding</span></span>|<span data-ttu-id="02ac8-164">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-164">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="02ac8-165">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="02ac8-165">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="02ac8-166">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="02ac8-166">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="02ac8-167">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="02ac8-167">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="02ac8-168">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="02ac8-168">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="02ac8-169">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-169">The default is UTF8.</span></span> <span data-ttu-id="02ac8-170">Bu öznitelik türü <xref:System.Text.Encoding> ..</span><span class="sxs-lookup"><span data-stu-id="02ac8-170">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="02ac8-171">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="02ac8-171">transactionFlow</span></span>|<span data-ttu-id="02ac8-172">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="02ac8-172">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="02ac8-173">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="02ac8-173">The default is `false`.</span></span>|
|<span data-ttu-id="02ac8-174">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="02ac8-174">useDefaultWebProxy</span></span>|<span data-ttu-id="02ac8-175">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="02ac8-175">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="02ac8-176">Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="02ac8-176">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="02ac8-177">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="02ac8-177">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="02ac8-178">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02ac8-178">Child Elements</span></span>

|<span data-ttu-id="02ac8-179">Öğe</span><span class="sxs-lookup"><span data-stu-id="02ac8-179">Element</span></span>|<span data-ttu-id="02ac8-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02ac8-180">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="02ac8-181">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-181">Defines the security settings for the message.</span></span> <span data-ttu-id="02ac8-182">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-182">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="02ac8-183">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-183">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="02ac8-184">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-184">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="02ac8-185">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-185">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="02ac8-186">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02ac8-186">Parent Elements</span></span>

|<span data-ttu-id="02ac8-187">Öğe</span><span class="sxs-lookup"><span data-stu-id="02ac8-187">Element</span></span>|<span data-ttu-id="02ac8-188">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02ac8-188">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="02ac8-189">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-189">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="02ac8-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02ac8-190">Remarks</span></span>

<span data-ttu-id="02ac8-191">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla sistem genelinde kimlik paylaşma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-191">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="02ac8-192">Bu kimlikler, kullanıcılara veya makinelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-192">These identities can refer to users or to machines.</span></span> <span data-ttu-id="02ac8-193">Federasyon HTTP, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini kullanarak özel olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="02ac8-193">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="02ac8-194">Bu bağlama WS-Federation protokolü için Windows Communication Foundation (WCF) desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-194">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="02ac8-195">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-195">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="02ac8-196">Bağlamalar bağlama öğelerinden oluşan bir yığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="02ac8-196">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="02ac8-197">İçindeki bağlama öğelerinin yığını</span><span class="sxs-lookup"><span data-stu-id="02ac8-197">The stack of binding elements in</span></span>

<span data-ttu-id="02ac8-198">`wsFederationHttpBinding`, içinde bulunan ile aynıdır`wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="02ac8-198">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="02ac8-199">ne zaman [\<security>](security-of-wsfederationhttpbinding.md) varsayılan değerine ayarlanır <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .</span><span class="sxs-lookup"><span data-stu-id="02ac8-199">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="02ac8-200">, `wsFederationHttpBinding` ' Deki ileti güvenliği ayarlarının ayrıntılarını denetler [\<message>](message-element-of-wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="02ac8-200">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="02ac8-201">[\<security>](security-of-wsfederationhttpbinding.md)Öğesi, bağlama oluşturulduktan sonra bağlama tarafından kullanılan güvenlik değiştirilemez olarak yalnızca erişim sunmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="02ac8-201">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="02ac8-202">`wsFederationHttpBinding`Ayrıca, gizlilik bildiriminin bulunduğu URI 'yi ayarlamak ve almak için bir privacyNoticeAt özniteliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="02ac8-202">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="02ac8-203">İlkenin güvenli tutulması, Federasyon senaryolarında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-203">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="02ac8-204">Bu öneri, ilkeyi kötü amaçlı kullanıcılardan korumak için HTTPS gibi bir güvenlik biçimi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="02ac8-204">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="02ac8-205">Bu bağlamayı kullanan Federasyon senaryolarında, hizmet ilkesi potansiyel olarak, verilen (SAML) belirtecini şifrelemek için kullanılan anahtar, belirtece yerleştirilecek talepler türü ve benzeri önemli bilgilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-205">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="02ac8-206">Bu ilke ile oynanabilir bir saldırgan, verilen belirtecin anahtarını daha fazla değişiklik, bilgi açığa çıkması ve diğer kötü amaçlı davranışa göre bulabilir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-206">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="02ac8-207">Bunu önlemeye yardımcı olmak için, ilkenin hizmetten güvenli bir şekilde (örneğin, HTTPS kullanılarak) alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02ac8-207">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="02ac8-208">Bu bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="02ac8-208">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="02ac8-209">Örnek</span><span class="sxs-lookup"><span data-stu-id="02ac8-209">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="02ac8-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02ac8-210">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="02ac8-211">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02ac8-211">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="02ac8-212">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="02ac8-212">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02ac8-213">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02ac8-213">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="02ac8-214">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="02ac8-214">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
