---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 60ce3cdfd7c78d152c71cdd652532cc96a6be296
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481125"
---
# <a name="custombinding"></a><span data-ttu-id="73254-101">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="73254-101">\<customBinding></span></span>

<span data-ttu-id="73254-102">Kullanıcı için Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="73254-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="73254-103">\<system.serviceModel > \\</span><span class="sxs-lookup"><span data-stu-id="73254-103">\<system.serviceModel>\\</span></span>
<span data-ttu-id="73254-104">\<bağlamaları > \\</span><span class="sxs-lookup"><span data-stu-id="73254-104">\<bindings>\\</span></span>
<span data-ttu-id="73254-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="73254-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="73254-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73254-106">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73254-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73254-107">Attributes and Elements</span></span>

<span data-ttu-id="73254-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73254-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="73254-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73254-109">Attributes</span></span>

|<span data-ttu-id="73254-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73254-110">Attribute</span></span>|<span data-ttu-id="73254-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73254-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="73254-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="73254-112">closeTimeout</span></span>|<span data-ttu-id="73254-113">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="73254-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="73254-114">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="73254-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73254-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="73254-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="73254-116">name</span><span class="sxs-lookup"><span data-stu-id="73254-116">name</span></span>|<span data-ttu-id="73254-117">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="73254-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="73254-118">Özel bağlama için kimlik dizesi görür kullanıcı tanımlı bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="73254-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="73254-119">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="73254-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="73254-120">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="73254-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="73254-121">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="73254-121">openTimeout</span></span>|<span data-ttu-id="73254-122">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="73254-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="73254-123">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="73254-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73254-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="73254-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="73254-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="73254-125">receiveTimeout</span></span>|<span data-ttu-id="73254-126">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="73254-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="73254-127">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="73254-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73254-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="73254-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="73254-129">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="73254-129">sendTimeout</span></span>|<span data-ttu-id="73254-130">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="73254-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="73254-131">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="73254-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="73254-132">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="73254-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="73254-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73254-133">Child Elements</span></span>

|<span data-ttu-id="73254-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="73254-134">Element</span></span>|<span data-ttu-id="73254-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73254-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73254-136">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="73254-136">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="73254-137">Özel bağlama için iki yönlü Mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="73254-138">Çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73254-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="73254-139">TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="73254-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="73254-140">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73254-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="73254-141">Bu istemci adresi tarafından sağlanan `ClientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="73254-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="73254-142">Bu öğe türünde <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="73254-143">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="73254-143">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="73254-144">Bir Eş Adı Çözümleme Protokolü (PNRP) eş ad çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="73254-145">Bu öğe türünde <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="73254-146">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="73254-146">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="73254-147">WS-Reliable Mesajlaşma için ayarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="73254-148">Bu öğe için özel bir bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekler-bir kez teslim Güvenceleri.</span><span class="sxs-lookup"><span data-stu-id="73254-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="73254-149">Bu öğe türünde <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="73254-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="73254-150">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="73254-151">Özel bağlama güvenliği için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="73254-152">Bu öğe türünde <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="73254-153">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="73254-153">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="73254-154">SSL akışı bağlama için güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="73254-155">Bu öğe türünde <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="73254-156">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="73254-156">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="73254-157">Bağlama tarafından kullanılacak protokolü ve işlem akışı desteklediğini belirtir `transactionProtocol` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="73254-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="73254-158">Bu öğe türünde <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="73254-159">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="73254-159">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="73254-160">Özel bağlama güvenliği akış seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73254-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="73254-161">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="73254-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73254-162">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73254-162">Parent Elements</span></span>

|<span data-ttu-id="73254-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="73254-163">Element</span></span>|<span data-ttu-id="73254-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73254-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="73254-165">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="73254-165">bindings</span></span>|<span data-ttu-id="73254-166">Windows Communication Foundation uygulamaları için tüm bağlamaları içeriyor.</span><span class="sxs-lookup"><span data-stu-id="73254-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73254-167">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73254-167">Remarks</span></span>

<span data-ttu-id="73254-168">Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="73254-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="73254-169">Özel olarak uyarlanmış bağlamaları my belirli varlıklar için yapılandırma öğeleri ekleme oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="73254-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="73254-170">Örneğin, kullanıcı birleştirebilirsiniz `httpsTransport` bölümünde `reliableSession` bölümü ve `security` güvenilir ve güvenli bir https oluşturulacak bölüm tabanlı bağlama.</span><span class="sxs-lookup"><span data-stu-id="73254-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="73254-171">Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73254-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="73254-172">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="73254-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="73254-173">Her özel bağlama bir ve yalnızca bir transport öğesi olmalı.</span><span class="sxs-lookup"><span data-stu-id="73254-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="73254-174">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="73254-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="73254-175">Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="73254-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="73254-176">Önerilen yığın öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="73254-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="73254-177">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="73254-177">Transactions (optional)</span></span>

2. <span data-ttu-id="73254-178">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="73254-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="73254-179">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="73254-179">Security (optional)</span></span>

4. <span data-ttu-id="73254-180">Taşıma</span><span class="sxs-lookup"><span data-stu-id="73254-180">Transport</span></span>

5. <span data-ttu-id="73254-181">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="73254-181">Encoder (optional)</span></span>

<span data-ttu-id="73254-182">Sistem tarafından sağlanan bağlamalar birini hizmetinizin gereksinimlerini karşılamıyor, özel bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="73254-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="73254-183">Özel bağlama, örneğin, yeni bir taşıma veya bir hizmet uç noktasında yeni bir kodlayıcı kullanımını etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73254-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="73254-184">Özel bağlama birini kullanarak oluşturulan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırayla dizilir" öğelerinin bir koleksiyondan:</span><span class="sxs-lookup"><span data-stu-id="73254-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="73254-185">En üstünde isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akmasını sağlayan işlem.</span><span class="sxs-lookup"><span data-stu-id="73254-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="73254-186">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve mekanizması WS-ReliableMessaging belirtiminde tanımlanan sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="73254-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="73254-187">Bu kavramı bir oturumu SOAP ve aktarım aracılar çapraz.</span><span class="sxs-lookup"><span data-stu-id="73254-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="73254-188">Sonraki yetkilendirme, kimlik doğrulaması, koruma ve gizlilik gibi güvenlik özellikleri sunan bir isteğe bağlı güvenlik bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="73254-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="73254-189">Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="73254-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="73254-190">Sonraki isteğe bağlı ileti desenleri bağlama öğeleri tarafından belirtilir:</span><span class="sxs-lookup"><span data-stu-id="73254-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="73254-191">Sonraki yükseltmeleri/Yardımcıları isteğe bağlı aktarım bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="73254-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="73254-192">Sonraki gerekli ileti kodlama bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="73254-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="73254-193">Kendi aktarımı kullanın veya bağlamaları aşağıdaki kodlamasını birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="73254-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="73254-194">Altta bir gerekli aktarım öğesidir.</span><span class="sxs-lookup"><span data-stu-id="73254-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="73254-195">Kendi aktarımı kullanın ya da bağlama öğelerinin Windows Communication Foundation (WCF) tarafından sağlanan aktarım birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="73254-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="73254-196">Aşağıdaki tabloda, her katman için seçenekler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="73254-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="73254-197">Katman</span><span class="sxs-lookup"><span data-stu-id="73254-197">Layer</span></span>|<span data-ttu-id="73254-198">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="73254-198">Options</span></span>|<span data-ttu-id="73254-199">Gerekli</span><span class="sxs-lookup"><span data-stu-id="73254-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="73254-200">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="73254-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="73254-201">Hayır</span><span class="sxs-lookup"><span data-stu-id="73254-201">No</span></span>|
|<span data-ttu-id="73254-202">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="73254-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="73254-203">Hayır</span><span class="sxs-lookup"><span data-stu-id="73254-203">No</span></span>|
|<span data-ttu-id="73254-204">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="73254-204">Security</span></span>|<span data-ttu-id="73254-205">Simetrik, asimetrik, aktarım düzeyinde</span><span class="sxs-lookup"><span data-stu-id="73254-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="73254-206">Hayır</span><span class="sxs-lookup"><span data-stu-id="73254-206">No</span></span>|
|<span data-ttu-id="73254-207">Şeklini değiştirme</span><span class="sxs-lookup"><span data-stu-id="73254-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="73254-208">Hayır</span><span class="sxs-lookup"><span data-stu-id="73254-208">No</span></span>|
|<span data-ttu-id="73254-209">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="73254-209">Transport Upgrades</span></span>|<span data-ttu-id="73254-210">SSL akışı, Windows stream eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="73254-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="73254-211">Hayır</span><span class="sxs-lookup"><span data-stu-id="73254-211">No</span></span>|
|<span data-ttu-id="73254-212">Encoding</span><span class="sxs-lookup"><span data-stu-id="73254-212">Encoding</span></span>|<span data-ttu-id="73254-213">İkili, MTOM, özel bir metin</span><span class="sxs-lookup"><span data-stu-id="73254-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="73254-214">Evet</span><span class="sxs-lookup"><span data-stu-id="73254-214">Yes</span></span>|
|<span data-ttu-id="73254-215">Taşıma</span><span class="sxs-lookup"><span data-stu-id="73254-215">Transport</span></span>|<span data-ttu-id="73254-216">TCP ve adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel türde</span><span class="sxs-lookup"><span data-stu-id="73254-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="73254-217">Evet</span><span class="sxs-lookup"><span data-stu-id="73254-217">Yes</span></span>|

<span data-ttu-id="73254-218">Ayrıca, kendi bağlama öğeleri tanımlayıp bunları herhangi bir önceki tanımlanmış katmanları arasında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73254-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="73254-219">Bir özel sistem tarafından sağlanan bir bağlamayı değiştirmek için bağlama kullanma hakkında bir tartışma için bkz. [nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="73254-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73254-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73254-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="73254-221">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="73254-221">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="73254-222">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="73254-222">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="73254-223">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="73254-223">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="73254-224">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="73254-224">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="73254-225">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="73254-225">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="73254-226">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="73254-226">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="73254-227">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="73254-227">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="73254-228">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="73254-228">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
