---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 766dab35541465da15ccb1090d41b22332aafd0e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739044"
---
# <a name="custombinding"></a><span data-ttu-id="b8c77-101">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b8c77-101">\<customBinding></span></span>

<span data-ttu-id="b8c77-102">Kullanıcı için mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8c77-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="b8c77-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b8c77-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8c77-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b8c77-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b8c77-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b8c77-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b8c77-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customBinding >**</span><span class="sxs-lookup"><span data-stu-id="b8c77-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b8c77-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8c77-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b8c77-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8c77-108">Attributes and Elements</span></span>

<span data-ttu-id="b8c77-109">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b8c77-109">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="b8c77-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8c77-110">Attributes</span></span>

|<span data-ttu-id="b8c77-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8c77-111">Attribute</span></span>|<span data-ttu-id="b8c77-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8c77-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b8c77-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="b8c77-113">closeTimeout</span></span>|<span data-ttu-id="b8c77-114">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="b8c77-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b8c77-115">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8c77-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-116">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b8c77-117">name</span><span class="sxs-lookup"><span data-stu-id="b8c77-117">name</span></span>|<span data-ttu-id="b8c77-118">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b8c77-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b8c77-119">Bu değer, özel bağlama için kimlik dizesi görevi gören Kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="b8c77-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b8c77-121">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="b8c77-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="b8c77-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="b8c77-122">openTimeout</span></span>|<span data-ttu-id="b8c77-123">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="b8c77-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b8c77-124">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8c77-125">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b8c77-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="b8c77-126">receiveTimeout</span></span>|<span data-ttu-id="b8c77-127">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="b8c77-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b8c77-128">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8c77-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-129">The default is 00:01:00.</span></span>|
|<span data-ttu-id="b8c77-130">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="b8c77-130">sendTimeout</span></span>|<span data-ttu-id="b8c77-131">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="b8c77-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b8c77-132">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8c77-133">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-133">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b8c77-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8c77-134">Child Elements</span></span>

|<span data-ttu-id="b8c77-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8c77-135">Element</span></span>|<span data-ttu-id="b8c77-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8c77-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8c77-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="b8c77-137">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="b8c77-138">Özel bağlamaya iki yönlü mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="b8c77-139">Çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="b8c77-140">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="b8c77-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="b8c77-141">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="b8c77-142">Bu istemci adresi `ClientBaseAddress` özniteliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="b8c77-143">Bu öğe <xref:System.ServiceModel.Configuration.CompositeDuplexElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="b8c77-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="b8c77-144">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="b8c77-145">Eş adı çözümleme Protokolü (PNRP) eş adı çözümleyicisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="b8c77-146">Bu öğe <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="b8c77-147">Reliableoturum > \<</span><span class="sxs-lookup"><span data-stu-id="b8c77-147">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="b8c77-148">WS-güvenilir mesajlaşma için ayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="b8c77-149">Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="b8c77-150">Bu öğe <xref:System.ServiceModel.Configuration.ReliableSessionElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="b8c77-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b8c77-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="b8c77-152">Özel bağlamanın güvenliği için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="b8c77-153">Bu öğe <xref:System.ServiceModel.Configuration.SecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="b8c77-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="b8c77-154">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="b8c77-155">SSL akışı bağlamasının güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="b8c77-156">Bu öğe <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="b8c77-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="b8c77-157">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="b8c77-158">Bağlamanın işlem akışını ve `transactionProtocol` özniteliği tarafından kullanılacak protokolü desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="b8c77-159">Bu öğe <xref:System.ServiceModel.Configuration.TransactionFlowElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="b8c77-160">windowsStreamSecurity > \<</span><span class="sxs-lookup"><span data-stu-id="b8c77-160">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="b8c77-161">Özel bağlamanın akış güvenliğini sağlama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="b8c77-162">Bu öğe <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8c77-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8c77-163">Parent Elements</span></span>

|<span data-ttu-id="b8c77-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8c77-164">Element</span></span>|<span data-ttu-id="b8c77-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8c77-165">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="b8c77-166">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8c77-166">bindings</span></span>|<span data-ttu-id="b8c77-167">Windows Communication Foundation uygulamaların tüm bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8c77-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8c77-168">Remarks</span></span>

<span data-ttu-id="b8c77-169">Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8c77-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="b8c77-170">Özel uyarlanmış bağlamalar, belirli varlıklar için yapılandırma öğelerini eklemem oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="b8c77-171">Örneğin, Kullanıcı, güvenilir ve güvenli bir https tabanlı bağlama oluşturmak için `httpsTransport` bölümünü, `reliableSession` bölümünü ve `security` bölümünü birleştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="b8c77-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="b8c77-172">Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8c77-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="b8c77-173">Her öğe, yığının bir öğesini tanımlar ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="b8c77-174">Her özel bağlamada bir ve yalnızca bir Transport öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="b8c77-175">Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b8c77-175">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="b8c77-176">Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek?</span><span class="sxs-lookup"><span data-stu-id="b8c77-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="b8c77-177">Yığın öğelerinin önerilen sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b8c77-177">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="b8c77-178">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b8c77-178">Transactions (optional)</span></span>

2. <span data-ttu-id="b8c77-179">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b8c77-179">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="b8c77-180">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b8c77-180">Security (optional)</span></span>

4. <span data-ttu-id="b8c77-181">Aktarım</span><span class="sxs-lookup"><span data-stu-id="b8c77-181">Transport</span></span>

5. <span data-ttu-id="b8c77-182">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="b8c77-182">Encoder (optional)</span></span>

<span data-ttu-id="b8c77-183">Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında özel bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8c77-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="b8c77-184">Bir hizmet uç noktasında yeni bir taşımanın veya yeni bir kodlayıcının kullanımını etkinleştirmek için, örneğin, özel bir bağlama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="b8c77-185">Özel bir bağlama, belirli bir sırada "yığılmış" olan bağlama öğeleri koleksiyonundan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> biri kullanılarak oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="b8c77-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="b8c77-186">En üstte, akan işlemlere izin veren isteğe bağlı bir <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b8c77-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="b8c77-187">Next, WS-ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizması sağlayan isteğe bağlı bir <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b8c77-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="b8c77-188">Bu oturum kavramı, SOAP ve aktarım aracıları arasında geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="b8c77-189">Daha sonra yetkilendirme, kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir güvenlik bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="b8c77-190">Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="b8c77-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="b8c77-191">Daha sonra bağlama öğeleri tarafından belirtilen isteğe bağlı ileti desenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b8c77-191">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="b8c77-192">Daha sonra isteğe bağlı taşıma yükseltmeleri/yardımcıları bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b8c77-192">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="b8c77-193">Next, gerekli bir ileti kodlama bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="b8c77-194">Kendi taşıyıcıyı kullanabilir veya aşağıdaki ileti kodlama bağlamalarından birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8c77-194">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="b8c77-195">En altta gerekli bir taşıma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="b8c77-196">Kendi taşıyıcıyı kullanabilir veya Windows Communication Foundation (WCF) tarafından sunulan taşıma bağlama öğelerinden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b8c77-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="b8c77-197">Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8c77-197">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="b8c77-198">Katmanı</span><span class="sxs-lookup"><span data-stu-id="b8c77-198">Layer</span></span>|<span data-ttu-id="b8c77-199">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b8c77-199">Options</span></span>|<span data-ttu-id="b8c77-200">Gerekli</span><span class="sxs-lookup"><span data-stu-id="b8c77-200">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="b8c77-201">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="b8c77-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="b8c77-202">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8c77-202">No</span></span>|
|<span data-ttu-id="b8c77-203">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="b8c77-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="b8c77-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8c77-204">No</span></span>|
|<span data-ttu-id="b8c77-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b8c77-205">Security</span></span>|<span data-ttu-id="b8c77-206">Simetrik, asimetrik, aktarım düzeyi</span><span class="sxs-lookup"><span data-stu-id="b8c77-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="b8c77-207">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8c77-207">No</span></span>|
|<span data-ttu-id="b8c77-208">Şekil değişikliği</span><span class="sxs-lookup"><span data-stu-id="b8c77-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="b8c77-209">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8c77-209">No</span></span>|
|<span data-ttu-id="b8c77-210">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="b8c77-210">Transport Upgrades</span></span>|<span data-ttu-id="b8c77-211">SSL akışı, Windows Stream, eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="b8c77-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="b8c77-212">Hayır</span><span class="sxs-lookup"><span data-stu-id="b8c77-212">No</span></span>|
|<span data-ttu-id="b8c77-213">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="b8c77-213">Encoding</span></span>|<span data-ttu-id="b8c77-214">Metin, Ikili, MTOM, özel</span><span class="sxs-lookup"><span data-stu-id="b8c77-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="b8c77-215">Evet</span><span class="sxs-lookup"><span data-stu-id="b8c77-215">Yes</span></span>|
|<span data-ttu-id="b8c77-216">Aktarım</span><span class="sxs-lookup"><span data-stu-id="b8c77-216">Transport</span></span>|<span data-ttu-id="b8c77-217">TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel</span><span class="sxs-lookup"><span data-stu-id="b8c77-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="b8c77-218">Evet</span><span class="sxs-lookup"><span data-stu-id="b8c77-218">Yes</span></span>|

<span data-ttu-id="b8c77-219">Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8c77-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="b8c77-220">Sistem tarafından sağlanmış bir bağlamayı değiştirmek için özel bağlama kullanma hakkında tartışma için bkz. [nasıl yapılır: sistem tarafından belirtilen bağlamayı özelleştirme](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="b8c77-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8c77-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8c77-221">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b8c77-222">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="b8c77-222">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="b8c77-223">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8c77-223">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b8c77-224">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b8c77-224">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b8c77-225">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8c77-225">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b8c77-226">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="b8c77-226">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="b8c77-227">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b8c77-227">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b8c77-228">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8c77-228">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b8c77-229">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8c77-229">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
