---
title: '&lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: c927ba59ccdb6e5a717fcaccde9294845a2c41cc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153910"
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="2dcc6-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2dcc6-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="2dcc6-103">Kullanıcı için Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="2dcc6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2dcc6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2dcc6-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-105">\<bindings></span></span>  
<span data-ttu-id="2dcc6-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dcc6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dcc6-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
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
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dcc6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dcc6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2dcc6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dcc6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2dcc6-110">Attributes</span></span>  
  
|<span data-ttu-id="2dcc6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2dcc6-111">Attribute</span></span>|<span data-ttu-id="2dcc6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2dcc6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2dcc6-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="2dcc6-113">closeTimeout</span></span>|<span data-ttu-id="2dcc6-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2dcc6-115">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2dcc6-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2dcc6-117">name</span><span class="sxs-lookup"><span data-stu-id="2dcc6-117">name</span></span>|<span data-ttu-id="2dcc6-118">Bağlama yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2dcc6-119">Özel bağlama için kimlik dizesi görür kullanıcı tanımlı bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="2dcc6-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2dcc6-121">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2dcc6-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="2dcc6-122">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="2dcc6-122">openTimeout</span></span>|<span data-ttu-id="2dcc6-123">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2dcc6-124">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2dcc6-125">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2dcc6-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2dcc6-126">receiveTimeout</span></span>|<span data-ttu-id="2dcc6-127">A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2dcc6-128">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2dcc6-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2dcc6-130">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="2dcc6-130">sendTimeout</span></span>|<span data-ttu-id="2dcc6-131">A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2dcc6-132">Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2dcc6-133">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2dcc6-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dcc6-134">Child Elements</span></span>  
  
|<span data-ttu-id="2dcc6-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="2dcc6-135">Element</span></span>|<span data-ttu-id="2dcc6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2dcc6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2dcc6-137">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="2dcc6-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="2dcc6-138">Özel bağlama için iki yönlü Mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="2dcc6-139">Çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="2dcc6-140">TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="2dcc6-141">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="2dcc6-142">Bu istemci adresi tarafından sağlanan `ClientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="2dcc6-143">Bu öğe türünde <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="2dcc6-145">Bir Eş Adı Çözümleme Protokolü (PNRP) eş ad çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="2dcc6-146">Bu öğe türünde <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="2dcc6-148">WS-Reliable Mesajlaşma için ayarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="2dcc6-149">Bu öğe için özel bir bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekler-bir kez teslim Güvenceleri.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="2dcc6-150">Bu öğe türünde <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="2dcc6-152">Özel bağlama güvenliği için seçenekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="2dcc6-153">Bu öğe türünde <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="2dcc6-155">SSL akışı bağlama için güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="2dcc6-156">Bu öğe türünde <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="2dcc6-158">Bağlama tarafından kullanılacak protokolü ve işlem akışı desteklediğini belirtir `transactionProtocol` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="2dcc6-159">Bu öğe türünde <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="2dcc6-160">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="2dcc6-161">Özel bağlama güvenliği akış seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="2dcc6-162">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2dcc6-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dcc6-163">Parent Elements</span></span>  
  
|<span data-ttu-id="2dcc6-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="2dcc6-164">Element</span></span>|<span data-ttu-id="2dcc6-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2dcc6-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2dcc6-166">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2dcc6-166">bindings</span></span>|<span data-ttu-id="2dcc6-167">Windows Communication Foundation uygulamaları için tüm bağlamaları içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dcc6-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dcc6-168">Remarks</span></span>  
 <span data-ttu-id="2dcc6-169">Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="2dcc6-170">Özel olarak uyarlanmış bağlamaları my belirli varlıklar için yapılandırma öğeleri ekleme oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="2dcc6-171">Örneğin, kullanıcı birleştirebilirsiniz `httpsTransport` bölümünde `reliableSession` bölümü ve `security` güvenilir ve güvenli bir https oluşturulacak bölüm tabanlı bağlama.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="2dcc6-172">Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="2dcc6-173">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="2dcc6-174">Her özel bağlama bir ve yalnızca bir transport öğesi olmalı.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="2dcc6-175">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="2dcc6-176">Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="2dcc6-177">Önerilen yığın öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="2dcc6-178">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2dcc6-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="2dcc6-179">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2dcc6-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="2dcc6-180">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2dcc6-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="2dcc6-181">Taşıma</span><span class="sxs-lookup"><span data-stu-id="2dcc6-181">Transport</span></span>  
  
5.  <span data-ttu-id="2dcc6-182">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="2dcc6-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="2dcc6-183">Sistem tarafından sağlanan bağlamalar birini hizmetinizin gereksinimlerini karşılamıyor, özel bir bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="2dcc6-184">Özel bağlama, örneğin, yeni bir taşıma veya bir hizmet uç noktasında yeni bir kodlayıcı kullanımını etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="2dcc6-185">Özel bağlama birini kullanarak oluşturulan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırayla dizilir" öğelerinin bir koleksiyondan:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="2dcc6-186">En üstünde isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akmasını sağlayan işlem.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="2dcc6-187">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve mekanizması WS-ReliableMessaging belirtiminde tanımlanan sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="2dcc6-188">Bu kavramı bir oturumu SOAP ve aktarım aracılar çapraz.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="2dcc6-189">Sonraki yetkilendirme, kimlik doğrulaması, koruma ve gizlilik gibi güvenlik özellikleri sunan bir isteğe bağlı güvenlik bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="2dcc6-190">Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="2dcc6-191">Sonraki isteğe bağlı ileti desenleri bağlama öğeleri tarafından belirtilir:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="2dcc6-192">Sonraki yükseltmeleri/Yardımcıları isteğe bağlı aktarım bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="2dcc6-193">Sonraki gerekli ileti kodlama bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="2dcc6-194">Kendi aktarımı kullanın veya bağlamaları aşağıdaki kodlamasını birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="2dcc6-195">Altta bir gerekli aktarım öğesidir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="2dcc6-196">Kendi aktarımı kullanın ya da bağlama öğelerinin Windows Communication Foundation (WCF) tarafından sağlanan aktarım birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2dcc6-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="2dcc6-197">Aşağıdaki tabloda, her katman için seçenekler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="2dcc6-198">Katman</span><span class="sxs-lookup"><span data-stu-id="2dcc6-198">Layer</span></span>|<span data-ttu-id="2dcc6-199">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2dcc6-199">Options</span></span>|<span data-ttu-id="2dcc6-200">Gerekli</span><span class="sxs-lookup"><span data-stu-id="2dcc6-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="2dcc6-201">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="2dcc6-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="2dcc6-202">Hayır</span><span class="sxs-lookup"><span data-stu-id="2dcc6-202">No</span></span>|  
|<span data-ttu-id="2dcc6-203">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="2dcc6-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="2dcc6-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="2dcc6-204">No</span></span>|  
|<span data-ttu-id="2dcc6-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2dcc6-205">Security</span></span>|<span data-ttu-id="2dcc6-206">Simetrik, asimetrik, aktarım düzeyinde</span><span class="sxs-lookup"><span data-stu-id="2dcc6-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="2dcc6-207">Hayır</span><span class="sxs-lookup"><span data-stu-id="2dcc6-207">No</span></span>|  
|<span data-ttu-id="2dcc6-208">Şeklini değiştirme</span><span class="sxs-lookup"><span data-stu-id="2dcc6-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="2dcc6-209">Hayır</span><span class="sxs-lookup"><span data-stu-id="2dcc6-209">No</span></span>|  
|<span data-ttu-id="2dcc6-210">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="2dcc6-210">Transport Upgrades</span></span>|<span data-ttu-id="2dcc6-211">SSL akışı, Windows stream eş çözümleyici</span><span class="sxs-lookup"><span data-stu-id="2dcc6-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="2dcc6-212">Hayır</span><span class="sxs-lookup"><span data-stu-id="2dcc6-212">No</span></span>|  
|<span data-ttu-id="2dcc6-213">Encoding</span><span class="sxs-lookup"><span data-stu-id="2dcc6-213">Encoding</span></span>|<span data-ttu-id="2dcc6-214">İkili, MTOM, özel bir metin</span><span class="sxs-lookup"><span data-stu-id="2dcc6-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="2dcc6-215">Evet</span><span class="sxs-lookup"><span data-stu-id="2dcc6-215">Yes</span></span>|  
|<span data-ttu-id="2dcc6-216">Taşıma</span><span class="sxs-lookup"><span data-stu-id="2dcc6-216">Transport</span></span>|<span data-ttu-id="2dcc6-217">TCP ve adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel türde</span><span class="sxs-lookup"><span data-stu-id="2dcc6-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="2dcc6-218">Evet</span><span class="sxs-lookup"><span data-stu-id="2dcc6-218">Yes</span></span>|  
  
 <span data-ttu-id="2dcc6-219">Ayrıca, kendi bağlama öğeleri tanımlayıp bunları herhangi bir önceki tanımlanmış katmanları arasında ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="2dcc6-220">Bir özel sistem tarafından sağlanan bir bağlamayı değiştirmek için bağlama kullanma hakkında bir tartışma için bkz. [nasıl yapılır: Sistem tarafından sağlanan bir bağlamayı özelleştirme](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="2dcc6-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
    
  
## <a name="see-also"></a><span data-ttu-id="2dcc6-221">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dcc6-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2dcc6-222">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2dcc6-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="2dcc6-223">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2dcc6-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2dcc6-224">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2dcc6-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2dcc6-225">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2dcc6-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2dcc6-226">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="2dcc6-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="2dcc6-227">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2dcc6-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2dcc6-228">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2dcc6-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2dcc6-229">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2dcc6-229">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
