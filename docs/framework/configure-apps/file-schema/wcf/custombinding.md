---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140802"
---
# \<customBinding>

<span data-ttu-id="5cad1-101">Kullanıcı için mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cad1-101">Provides full control over the messaging stack for the user.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**  

## <a name="syntax"></a><span data-ttu-id="5cad1-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cad1-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="5cad1-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cad1-103">Attributes and Elements</span></span>

<span data-ttu-id="5cad1-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="5cad1-104">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="5cad1-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5cad1-105">Attributes</span></span>

|<span data-ttu-id="5cad1-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5cad1-106">Attribute</span></span>|<span data-ttu-id="5cad1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cad1-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="5cad1-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5cad1-108">closeTimeout</span></span>|<span data-ttu-id="5cad1-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5cad1-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5cad1-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5cad1-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-111">The default is 00:01:00.</span></span>|
|<span data-ttu-id="5cad1-112">name</span><span class="sxs-lookup"><span data-stu-id="5cad1-112">name</span></span>|<span data-ttu-id="5cad1-113">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5cad1-113">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5cad1-114">Bu değer, özel bağlama için kimlik dizesi görevi gören Kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-114">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="5cad1-115">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-115">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5cad1-116">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="5cad1-116">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="5cad1-117">openTimeout</span><span class="sxs-lookup"><span data-stu-id="5cad1-117">openTimeout</span></span>|<span data-ttu-id="5cad1-118">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5cad1-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5cad1-119">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5cad1-120">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-120">The default is 00:01:00.</span></span>|
|<span data-ttu-id="5cad1-121">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5cad1-121">receiveTimeout</span></span>|<span data-ttu-id="5cad1-122"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5cad1-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5cad1-123">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5cad1-124">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-124">The default is 00:01:00.</span></span>|
|<span data-ttu-id="5cad1-125">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="5cad1-125">sendTimeout</span></span>|<span data-ttu-id="5cad1-126"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5cad1-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5cad1-127">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5cad1-128">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-128">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5cad1-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cad1-129">Child Elements</span></span>

|<span data-ttu-id="5cad1-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="5cad1-130">Element</span></span>|<span data-ttu-id="5cad1-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cad1-131">Description</span></span>|
|-------------|-----------------|
|[\<compositeDuplex>](compositeduplex.md)|<span data-ttu-id="5cad1-132">Özel bağlamaya iki yönlü mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-132">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="5cad1-133">Çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-133">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="5cad1-134">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5cad1-134">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="5cad1-135">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-135">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="5cad1-136">Bu istemci adresi özniteliği tarafından sağlanır `ClientBaseAddress` .</span><span class="sxs-lookup"><span data-stu-id="5cad1-136">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="5cad1-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CompositeDuplexElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-137">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[\<pnrpPeerResolver>](pnrppeerresolver.md)|<span data-ttu-id="5cad1-138">Eş adı çözümleme Protokolü (PNRP) eş adı çözümleyicisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-138">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="5cad1-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-139">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[\<reliableSession>](reliablesession.md)|<span data-ttu-id="5cad1-140">WS-güvenilir mesajlaşma için ayarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-140">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="5cad1-141">Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-141">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="5cad1-142">Bu öğe türündedir <xref:System.ServiceModel.Configuration.ReliableSessionElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-142">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="5cad1-143">Özel bağlamanın güvenliği için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-143">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="5cad1-144">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-144">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[\<sslStreamSecurity>](sslstreamsecurity.md)|<span data-ttu-id="5cad1-145">SSL akışı bağlamasının güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-145">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="5cad1-146">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-146">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[\<transactionFlow>](transactionflow.md)|<span data-ttu-id="5cad1-147">Bağlamanın işlem akışını desteklediğini ve özniteliği tarafından kullanılacak protokolü belirtir `transactionProtocol` .</span><span class="sxs-lookup"><span data-stu-id="5cad1-147">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="5cad1-148">Bu öğe türündedir <xref:System.ServiceModel.Configuration.TransactionFlowElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-148">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[\<windowsStreamSecurity>](windowsstreamsecurity.md)|<span data-ttu-id="5cad1-149">Özel bağlamanın akış güvenliğini sağlama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-149">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="5cad1-150">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="5cad1-150">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5cad1-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cad1-151">Parent Elements</span></span>

|<span data-ttu-id="5cad1-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="5cad1-152">Element</span></span>|<span data-ttu-id="5cad1-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cad1-153">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="5cad1-154">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5cad1-154">bindings</span></span>|<span data-ttu-id="5cad1-155">Windows Communication Foundation uygulamaların tüm bağlamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-155">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5cad1-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cad1-156">Remarks</span></span>

<span data-ttu-id="5cad1-157">Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cad1-157">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="5cad1-158">Özel uyarlanmış bağlamalar, belirli varlıklar için yapılandırma öğelerini eklemem oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-158">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="5cad1-159">Örneğin, Kullanıcı, `httpsTransport` `reliableSession` `security` güvenilir ve güvenli bir https tabanlı bağlama oluşturmak için bölümü, bölümü ve bölümünü birleştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="5cad1-159">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="5cad1-160">Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5cad1-160">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="5cad1-161">Her öğe, yığının bir öğesini tanımlar ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-161">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="5cad1-162">Her özel bağlamada bir ve yalnızca bir Transport öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-162">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="5cad1-163">Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-163">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="5cad1-164">Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek?</span><span class="sxs-lookup"><span data-stu-id="5cad1-164">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="5cad1-165">Yığın öğelerinin önerilen sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5cad1-165">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="5cad1-166">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5cad1-166">Transactions (optional)</span></span>

2. <span data-ttu-id="5cad1-167">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5cad1-167">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="5cad1-168">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5cad1-168">Security (optional)</span></span>

4. <span data-ttu-id="5cad1-169">Aktarım</span><span class="sxs-lookup"><span data-stu-id="5cad1-169">Transport</span></span>

5. <span data-ttu-id="5cad1-170">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="5cad1-170">Encoder (optional)</span></span>

<span data-ttu-id="5cad1-171">Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında özel bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cad1-171">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="5cad1-172">Bir hizmet uç noktasında yeni bir taşımanın veya yeni bir kodlayıcının kullanımını etkinleştirmek için, örneğin, özel bir bağlama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-172">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="5cad1-173">Özel bir bağlama, <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> belirli bir sırada "yığılmış" olan bağlama öğeleri koleksiyonundan biri kullanılarak oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="5cad1-173">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="5cad1-174">En üstte, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akan işlemlere izin veren isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cad1-174">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="5cad1-175">Next, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> WS-ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizması sağlayan isteğe bağlı bir ektir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-175">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="5cad1-176">Bu oturum kavramı, SOAP ve aktarım aracıları arasında geçiş yapabilir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-176">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="5cad1-177">Daha sonra yetkilendirme, kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir güvenlik bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-177">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="5cad1-178">Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="5cad1-178">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="5cad1-179">Daha sonra bağlama öğeleri tarafından belirtilen isteğe bağlı ileti desenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cad1-179">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="5cad1-180">Daha sonra isteğe bağlı taşıma yükseltmeleri/yardımcıları bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5cad1-180">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="5cad1-181">Next, gerekli bir ileti kodlama bağlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-181">Next is a required message encoding binding element.</span></span> <span data-ttu-id="5cad1-182">Kendi taşıyıcıyı kullanabilir veya aşağıdaki ileti kodlama bağlamalarından birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5cad1-182">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="5cad1-183">En altta gerekli bir taşıma öğesidir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-183">At the bottom is a required transport element.</span></span> <span data-ttu-id="5cad1-184">Kendi taşıyıcıyı kullanabilir veya Windows Communication Foundation (WCF) tarafından sunulan taşıma bağlama öğelerinden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5cad1-184">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="5cad1-185">Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cad1-185">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="5cad1-186">Katman</span><span class="sxs-lookup"><span data-stu-id="5cad1-186">Layer</span></span>|<span data-ttu-id="5cad1-187">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5cad1-187">Options</span></span>|<span data-ttu-id="5cad1-188">Gerekli</span><span class="sxs-lookup"><span data-stu-id="5cad1-188">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="5cad1-189">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="5cad1-189">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="5cad1-190">Hayır</span><span class="sxs-lookup"><span data-stu-id="5cad1-190">No</span></span>|
|<span data-ttu-id="5cad1-191">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="5cad1-191">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="5cad1-192">Hayır</span><span class="sxs-lookup"><span data-stu-id="5cad1-192">No</span></span>|
|<span data-ttu-id="5cad1-193">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="5cad1-193">Security</span></span>|<span data-ttu-id="5cad1-194">Simetrik, asimetrik, aktarım düzeyi</span><span class="sxs-lookup"><span data-stu-id="5cad1-194">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="5cad1-195">Hayır</span><span class="sxs-lookup"><span data-stu-id="5cad1-195">No</span></span>|
|<span data-ttu-id="5cad1-196">Şekil değişikliği</span><span class="sxs-lookup"><span data-stu-id="5cad1-196">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="5cad1-197">Hayır</span><span class="sxs-lookup"><span data-stu-id="5cad1-197">No</span></span>|
|<span data-ttu-id="5cad1-198">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="5cad1-198">Transport Upgrades</span></span>|<span data-ttu-id="5cad1-199">SSL akışı, Windows Stream, eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="5cad1-199">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="5cad1-200">Hayır</span><span class="sxs-lookup"><span data-stu-id="5cad1-200">No</span></span>|
|<span data-ttu-id="5cad1-201">Encoding</span><span class="sxs-lookup"><span data-stu-id="5cad1-201">Encoding</span></span>|<span data-ttu-id="5cad1-202">Metin, Ikili, MTOM, özel</span><span class="sxs-lookup"><span data-stu-id="5cad1-202">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="5cad1-203">Yes</span><span class="sxs-lookup"><span data-stu-id="5cad1-203">Yes</span></span>|
|<span data-ttu-id="5cad1-204">Aktarım</span><span class="sxs-lookup"><span data-stu-id="5cad1-204">Transport</span></span>|<span data-ttu-id="5cad1-205">TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel</span><span class="sxs-lookup"><span data-stu-id="5cad1-205">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="5cad1-206">Yes</span><span class="sxs-lookup"><span data-stu-id="5cad1-206">Yes</span></span>|

<span data-ttu-id="5cad1-207">Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cad1-207">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="5cad1-208">Sistem tarafından sağlanmış bir bağlamayı değiştirmek için özel bağlama kullanma hakkında tartışma için bkz. [nasıl yapılır: sistem tarafından belirtilen bağlamayı özelleştirme](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="5cad1-208">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5cad1-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cad1-209">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="5cad1-210">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5cad1-210">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5cad1-211">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5cad1-211">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5cad1-212">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5cad1-212">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5cad1-213">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="5cad1-213">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="5cad1-214">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5cad1-214">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5cad1-215">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5cad1-215">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5cad1-216">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5cad1-216">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
