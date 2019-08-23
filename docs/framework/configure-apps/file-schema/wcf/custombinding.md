---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 0b6f26c7b9e9d02b3ff20b53f42b09d671699ea5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919385"
---
# <a name="custombinding"></a><span data-ttu-id="3f09d-101">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3f09d-101">\<customBinding></span></span>

<span data-ttu-id="3f09d-102">Kullanıcı için mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f09d-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="3f09d-103">\<System. serviceModel > </span><span class="sxs-lookup"><span data-stu-id="3f09d-103">\<system.serviceModel></span></span>\
<span data-ttu-id="3f09d-104">\<bağlamalar > </span><span class="sxs-lookup"><span data-stu-id="3f09d-104">\<bindings></span></span>\
<span data-ttu-id="3f09d-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3f09d-105">\<customBinding></span></span>

## <a name="syntax"></a><span data-ttu-id="3f09d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f09d-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3f09d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f09d-107">Attributes and Elements</span></span>

<span data-ttu-id="3f09d-108">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3f09d-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="3f09d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f09d-109">Attributes</span></span>

|<span data-ttu-id="3f09d-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f09d-110">Attribute</span></span>|<span data-ttu-id="3f09d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f09d-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3f09d-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="3f09d-112">closeTimeout</span></span>|<span data-ttu-id="3f09d-113">Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3f09d-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3f09d-114">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3f09d-115">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-115">The default is 00:01:00.</span></span>|
|<span data-ttu-id="3f09d-116">name</span><span class="sxs-lookup"><span data-stu-id="3f09d-116">name</span></span>|<span data-ttu-id="3f09d-117">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3f09d-117">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3f09d-118">Bu değer, özel bağlama için kimlik dizesi görevi gören Kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-118">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="3f09d-119">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3f09d-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3f09d-120">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3f09d-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="3f09d-121">openTimeout</span><span class="sxs-lookup"><span data-stu-id="3f09d-121">openTimeout</span></span>|<span data-ttu-id="3f09d-122">Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3f09d-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3f09d-123">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3f09d-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="3f09d-125">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="3f09d-125">receiveTimeout</span></span>|<span data-ttu-id="3f09d-126">Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3f09d-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3f09d-127">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3f09d-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-128">The default is 00:01:00.</span></span>|
|<span data-ttu-id="3f09d-129">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="3f09d-129">sendTimeout</span></span>|<span data-ttu-id="3f09d-130">Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3f09d-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3f09d-131">Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3f09d-132">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-132">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3f09d-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f09d-133">Child Elements</span></span>

|<span data-ttu-id="3f09d-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f09d-134">Element</span></span>|<span data-ttu-id="3f09d-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f09d-135">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f09d-136">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="3f09d-136">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="3f09d-137">Özel bağlamaya iki yönlü mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-137">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="3f09d-138">Çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-138">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="3f09d-139">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3f09d-139">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="3f09d-140">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-140">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="3f09d-141">Bu istemci adresi `ClientBaseAddress` özniteliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-141">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="3f09d-142">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-142">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="3f09d-143">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="3f09d-143">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="3f09d-144">Eş adı çözümleme Protokolü (PNRP) eş adı çözümleyicisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-144">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="3f09d-145">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-145">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="3f09d-146">\<Reliableoturum ></span><span class="sxs-lookup"><span data-stu-id="3f09d-146">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="3f09d-147">WS-güvenilir mesajlaşma için ayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-147">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="3f09d-148">Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-148">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="3f09d-149">Bu öğe türündedir <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-149">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="3f09d-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3f09d-150">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="3f09d-151">Özel bağlamanın güvenliği için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-151">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="3f09d-152">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-152">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="3f09d-153">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="3f09d-153">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="3f09d-154">SSL akışı bağlamasının güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-154">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="3f09d-155">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-155">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="3f09d-156">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="3f09d-156">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="3f09d-157">Bağlamanın işlem akışını desteklediğini ve `transactionProtocol` özniteliği tarafından kullanılacak protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-157">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="3f09d-158">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-158">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="3f09d-159">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="3f09d-159">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="3f09d-160">Özel bağlamanın akış güvenliğini sağlama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-160">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="3f09d-161">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3f09d-161">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3f09d-162">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f09d-162">Parent Elements</span></span>

|<span data-ttu-id="3f09d-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f09d-163">Element</span></span>|<span data-ttu-id="3f09d-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f09d-164">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="3f09d-165">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f09d-165">bindings</span></span>|<span data-ttu-id="3f09d-166">Windows Communication Foundation uygulamaların tüm bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-166">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f09d-167">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f09d-167">Remarks</span></span>

<span data-ttu-id="3f09d-168">Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f09d-168">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="3f09d-169">Özel uyarlanmış bağlamalar, belirli varlıklar için yapılandırma öğelerini eklemem oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-169">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="3f09d-170">Örneğin, Kullanıcı, güvenilir ve güvenli bir `httpsTransport` https tabanlı `reliableSession` bağlama oluşturmak için `security` Bölümü, bölümü ve bölümünü birleştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="3f09d-170">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="3f09d-171">Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f09d-171">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="3f09d-172">Her öğe, yığının bir öğesini tanımlar ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-172">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="3f09d-173">Her özel bağlamada bir ve yalnızca bir Transport öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-173">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="3f09d-174">Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-174">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="3f09d-175">Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek?</span><span class="sxs-lookup"><span data-stu-id="3f09d-175">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="3f09d-176">Yığın öğelerinin önerilen sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3f09d-176">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="3f09d-177">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3f09d-177">Transactions (optional)</span></span>

2. <span data-ttu-id="3f09d-178">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3f09d-178">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="3f09d-179">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3f09d-179">Security (optional)</span></span>

4. <span data-ttu-id="3f09d-180">Aktarım</span><span class="sxs-lookup"><span data-stu-id="3f09d-180">Transport</span></span>

5. <span data-ttu-id="3f09d-181">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="3f09d-181">Encoder (optional)</span></span>

<span data-ttu-id="3f09d-182">Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında özel bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f09d-182">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="3f09d-183">Bir hizmet uç noktasında yeni bir taşımanın veya yeni bir kodlayıcının kullanımını etkinleştirmek için, örneğin, özel bir bağlama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-183">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="3f09d-184">Özel bir bağlama, <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> belirli bir sırada "yığılmış" olan bağlama öğeleri koleksiyonundan biri kullanılarak oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="3f09d-184">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="3f09d-185">En üstte, akan işlemlere izin <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> veren isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f09d-185">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="3f09d-186">Next, WS- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizması sağlayan isteğe bağlı bir ektir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-186">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="3f09d-187">Bu oturum kavramı, SOAP ve aktarım aracıları arasında geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-187">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="3f09d-188">Daha sonra yetkilendirme, kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir güvenlik bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-188">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="3f09d-189">Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="3f09d-189">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="3f09d-190">Daha sonra bağlama öğeleri tarafından belirtilen isteğe bağlı ileti desenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f09d-190">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="3f09d-191">Daha sonra isteğe bağlı taşıma yükseltmeleri/yardımcıları bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f09d-191">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="3f09d-192">Next, gerekli bir ileti kodlama bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-192">Next is a required message encoding binding element.</span></span> <span data-ttu-id="3f09d-193">Kendi taşıyıcıyı kullanabilir veya aşağıdaki ileti kodlama bağlamalarından birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f09d-193">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="3f09d-194">En altta gerekli bir taşıma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-194">At the bottom is a required transport element.</span></span> <span data-ttu-id="3f09d-195">Kendi taşıyıcıyı kullanabilir veya Windows Communication Foundation (WCF) tarafından sunulan taşıma bağlama öğelerinden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3f09d-195">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="3f09d-196">Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f09d-196">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="3f09d-197">Katman</span><span class="sxs-lookup"><span data-stu-id="3f09d-197">Layer</span></span>|<span data-ttu-id="3f09d-198">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3f09d-198">Options</span></span>|<span data-ttu-id="3f09d-199">Gerekli</span><span class="sxs-lookup"><span data-stu-id="3f09d-199">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="3f09d-200">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="3f09d-200">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="3f09d-201">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f09d-201">No</span></span>|
|<span data-ttu-id="3f09d-202">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="3f09d-202">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="3f09d-203">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f09d-203">No</span></span>|
|<span data-ttu-id="3f09d-204">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="3f09d-204">Security</span></span>|<span data-ttu-id="3f09d-205">Simetrik, asimetrik, aktarım düzeyi</span><span class="sxs-lookup"><span data-stu-id="3f09d-205">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="3f09d-206">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f09d-206">No</span></span>|
|<span data-ttu-id="3f09d-207">Şekil değişikliği</span><span class="sxs-lookup"><span data-stu-id="3f09d-207">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="3f09d-208">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f09d-208">No</span></span>|
|<span data-ttu-id="3f09d-209">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="3f09d-209">Transport Upgrades</span></span>|<span data-ttu-id="3f09d-210">SSL akışı, Windows Stream, eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="3f09d-210">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="3f09d-211">Hayır</span><span class="sxs-lookup"><span data-stu-id="3f09d-211">No</span></span>|
|<span data-ttu-id="3f09d-212">Encoding</span><span class="sxs-lookup"><span data-stu-id="3f09d-212">Encoding</span></span>|<span data-ttu-id="3f09d-213">Metin, Ikili, MTOM, özel</span><span class="sxs-lookup"><span data-stu-id="3f09d-213">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="3f09d-214">Evet</span><span class="sxs-lookup"><span data-stu-id="3f09d-214">Yes</span></span>|
|<span data-ttu-id="3f09d-215">Aktarım</span><span class="sxs-lookup"><span data-stu-id="3f09d-215">Transport</span></span>|<span data-ttu-id="3f09d-216">TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel</span><span class="sxs-lookup"><span data-stu-id="3f09d-216">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="3f09d-217">Evet</span><span class="sxs-lookup"><span data-stu-id="3f09d-217">Yes</span></span>|

<span data-ttu-id="3f09d-218">Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f09d-218">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="3f09d-219">Sistem tarafından sağlanmış bir bağlamayı değiştirmek için özel bağlama kullanma hakkında bir tartışma için bkz [. nasıl yapılır: Sistem tarafından sağlanmış bağlamayı](../../../wcf/extending/how-to-customize-a-system-provided-binding.md)özelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3f09d-219">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f09d-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f09d-220">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3f09d-221">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3f09d-221">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="3f09d-222">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f09d-222">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f09d-223">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3f09d-223">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3f09d-224">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f09d-224">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3f09d-225">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="3f09d-225">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="3f09d-226">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f09d-226">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f09d-227">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f09d-227">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3f09d-228">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f09d-228">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
