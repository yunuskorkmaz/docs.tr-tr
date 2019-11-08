---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 011a46c15785b7ffa832db57925c7e7b5f76c67a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732504"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="d3dfb-101">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d3dfb-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="d3dfb-102">WS-Federation destekleyen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="d3dfb-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d3dfb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3dfb-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d3dfb-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d3dfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d3dfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d3dfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsFederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="d3dfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="d3dfb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d3dfb-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3dfb-108">Attributes and Elements</span></span>

<span data-ttu-id="d3dfb-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3dfb-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3dfb-110">Attributes</span></span>

|<span data-ttu-id="d3dfb-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3dfb-111">Attribute</span></span>|<span data-ttu-id="d3dfb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3dfb-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d3dfb-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="d3dfb-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="d3dfb-114">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="d3dfb-115">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-115">The default is `false`.</span></span>|
|<span data-ttu-id="d3dfb-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="d3dfb-116">closeTimeout</span></span>|<span data-ttu-id="d3dfb-117">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d3dfb-118">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3dfb-119">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-119">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d3dfb-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d3dfb-120">hostnameComparisonMode</span></span>|<span data-ttu-id="d3dfb-121">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="d3dfb-122">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="d3dfb-123">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="d3dfb-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d3dfb-124">maxBufferPoolSize</span></span>|<span data-ttu-id="d3dfb-125">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d3dfb-126">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="d3dfb-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="d3dfb-127">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d3dfb-128">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d3dfb-129">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d3dfb-130">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="d3dfb-131">Değerini</span><span class="sxs-lookup"><span data-stu-id="d3dfb-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="d3dfb-132">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d3dfb-133">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="d3dfb-134">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d3dfb-135">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-135">The default is 65536.</span></span>|
|<span data-ttu-id="d3dfb-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="d3dfb-136">messageEncoding</span></span>|<span data-ttu-id="d3dfb-137">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="d3dfb-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d3dfb-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d3dfb-139">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="d3dfb-140">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="d3dfb-141">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="d3dfb-142">Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="d3dfb-143">name</span><span class="sxs-lookup"><span data-stu-id="d3dfb-143">name</span></span>|<span data-ttu-id="d3dfb-144">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d3dfb-145">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d3dfb-146">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d3dfb-147">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="d3dfb-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="d3dfb-148">openTimeout</span></span>|<span data-ttu-id="d3dfb-149">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d3dfb-150">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3dfb-151">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-151">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d3dfb-152">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="d3dfb-152">privacyNoticeAt</span></span>|<span data-ttu-id="d3dfb-153">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-153">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="d3dfb-154">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="d3dfb-154">privacyNoticeVersion</span></span>|<span data-ttu-id="d3dfb-155">Geçerli gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-155">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="d3dfb-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="d3dfb-156">proxyAddress</span></span>|<span data-ttu-id="d3dfb-157">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="d3dfb-158">`useDefaultWebProxy` `true`, bu ayar `null`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="d3dfb-159">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-159">The default is `null`.</span></span>|
|<span data-ttu-id="d3dfb-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="d3dfb-160">receiveTimeout</span></span>|<span data-ttu-id="d3dfb-161">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d3dfb-162">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3dfb-163">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-163">The default is 00:10:00.</span></span>|
|<span data-ttu-id="d3dfb-164">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="d3dfb-164">sendTimeout</span></span>|<span data-ttu-id="d3dfb-165">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d3dfb-166">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3dfb-167">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-167">The default is 00:01:00.</span></span>|
|<span data-ttu-id="d3dfb-168">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="d3dfb-168">textEncoding</span></span>|<span data-ttu-id="d3dfb-169">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d3dfb-170">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d3dfb-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d3dfb-171">-Bigendianunıcode: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="d3dfb-172">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="d3dfb-173">-UTF8:8 bit kodlama</span><span class="sxs-lookup"><span data-stu-id="d3dfb-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d3dfb-174">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-174">The default is UTF8.</span></span> <span data-ttu-id="d3dfb-175">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="d3dfb-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="d3dfb-176">transactionFlow</span></span>|<span data-ttu-id="d3dfb-177">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="d3dfb-178">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-178">The default is `false`.</span></span>|
|<span data-ttu-id="d3dfb-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="d3dfb-179">useDefaultWebProxy</span></span>|<span data-ttu-id="d3dfb-180">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="d3dfb-181">Bu öznitelik `true`, proxy adresi `null` olmalıdır (ayarlı değil).</span><span class="sxs-lookup"><span data-stu-id="d3dfb-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="d3dfb-182">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-182">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d3dfb-183">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3dfb-183">Child Elements</span></span>

|<span data-ttu-id="d3dfb-184">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3dfb-184">Element</span></span>|<span data-ttu-id="d3dfb-185">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3dfb-185">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3dfb-186">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d3dfb-186">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d3dfb-187">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-187">Defines the security settings for the message.</span></span> <span data-ttu-id="d3dfb-188">Bu öğe <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="d3dfb-189">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3dfb-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="d3dfb-190">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d3dfb-191">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="d3dfb-192">[Reliableoturum > \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d3dfb-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="d3dfb-193">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3dfb-194">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3dfb-194">Parent Elements</span></span>

|<span data-ttu-id="d3dfb-195">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3dfb-195">Element</span></span>|<span data-ttu-id="d3dfb-196">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3dfb-196">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3dfb-197">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="d3dfb-197">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d3dfb-198">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-198">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3dfb-199">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3dfb-199">Remarks</span></span>

<span data-ttu-id="d3dfb-200">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla sistem genelinde kimlik paylaşma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="d3dfb-201">Bu kimlikler, kullanıcılara veya makinelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="d3dfb-202">Federasyon HTTP, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini kullanarak özel olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="d3dfb-203">Bu bağlama WS-Federation protokolü için Windows Communication Foundation (WCF) desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="d3dfb-204">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-204">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="d3dfb-205">Bağlamalar bağlama öğelerinden oluşan bir yığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="d3dfb-206">İçindeki bağlama öğelerinin yığını</span><span class="sxs-lookup"><span data-stu-id="d3dfb-206">The stack of binding elements in</span></span>

<span data-ttu-id="d3dfb-207">`wsFederationHttpBinding`, `wsHttpBinding` içinde bulunan ile aynıdır</span><span class="sxs-lookup"><span data-stu-id="d3dfb-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="d3dfb-208">[\<güvenlik >](security-of-wsfederationhttpbinding.md) , <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>varsayılan değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-208">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="d3dfb-209">`wsFederationHttpBinding`, [\<message >](message-element-of-wsfederationhttpbinding.md)ileti güvenliği ayarlarının ayrıntılarını denetler.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="d3dfb-210">[\<güvenlik >](security-of-wsfederationhttpbinding.md) öğesinin yalnızca bağlama tarafından kullanılan güvenlik, bağlama oluşturulduktan sonra değiştirilemez olarak erişim sağladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-210">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="d3dfb-211">`wsFederationHttpBinding` Ayrıca, gizlilik bildiriminin bulunduğu URI 'yi ayarlamak ve almak için bir privacyNoticeAt özniteliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-211">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="d3dfb-212">İlkenin güvenli tutulması, Federasyon senaryolarında özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="d3dfb-213">Bu öneri, ilkeyi kötü amaçlı kullanıcılardan korumak için HTTPS gibi bir güvenlik biçimi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="d3dfb-214">Bu bağlamayı kullanan Federasyon senaryolarında, hizmet ilkesi potansiyel olarak, verilen (SAML) belirtecini şifrelemek için kullanılan anahtar, belirtece yerleştirilecek talepler türü ve benzeri önemli bilgilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="d3dfb-215">Bu ilke ile oynanabilir bir saldırgan, verilen belirtecin anahtarını daha fazla değişiklik, bilgi açığa çıkması ve diğer kötü amaçlı davranışa göre bulabilir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="d3dfb-216">Bunu önlemeye yardımcı olmak için, ilkenin hizmetten güvenli bir şekilde (örneğin, HTTPS kullanılarak) alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="d3dfb-217">Bu bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d3dfb-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="d3dfb-218">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3dfb-218">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d3dfb-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-219">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="d3dfb-220">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3dfb-220">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="d3dfb-221">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d3dfb-221">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3dfb-222">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d3dfb-222">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d3dfb-223">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d3dfb-223">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d3dfb-224">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="d3dfb-224">\<binding></span></span>](bindings.md)
