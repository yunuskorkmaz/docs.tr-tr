---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f73ad4d09e085040e006102e5b44664ece98a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="17f1a-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="17f1a-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="17f1a-103">Kullanıcı için Mesajlaşma yığın üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="17f1a-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="17f1a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="17f1a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="17f1a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="17f1a-105">\<bindings></span></span>  
<span data-ttu-id="17f1a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="17f1a-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f1a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17f1a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17f1a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="17f1a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17f1a-109">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="17f1a-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17f1a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="17f1a-110">Attributes</span></span>  
  
|<span data-ttu-id="17f1a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="17f1a-111">Attribute</span></span>|<span data-ttu-id="17f1a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17f1a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17f1a-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="17f1a-113">closeTimeout</span></span>|<span data-ttu-id="17f1a-114">A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="17f1a-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="17f1a-115">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="17f1a-116">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="17f1a-117">name</span><span class="sxs-lookup"><span data-stu-id="17f1a-117">name</span></span>|<span data-ttu-id="17f1a-118">Bağlama yapılandırma adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="17f1a-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="17f1a-119">Bu değer özel bağlama için kimlik dizesi olarak davranan bir kullanıcı tanımlı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="17f1a-120">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="17f1a-121">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="17f1a-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="17f1a-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="17f1a-122">openTimeout</span></span>|<span data-ttu-id="17f1a-123">A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="17f1a-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="17f1a-124">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="17f1a-125">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="17f1a-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="17f1a-126">receiveTimeout</span></span>|<span data-ttu-id="17f1a-127">A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="17f1a-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="17f1a-128">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="17f1a-129">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="17f1a-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="17f1a-130">sendTimeout</span></span>|<span data-ttu-id="17f1a-131">A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="17f1a-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="17f1a-132">Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="17f1a-133">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17f1a-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="17f1a-134">Child Elements</span></span>  
  
|<span data-ttu-id="17f1a-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="17f1a-135">Element</span></span>|<span data-ttu-id="17f1a-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17f1a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17f1a-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="17f1a-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="17f1a-138">İki yönlü özel bağlama Mesajlaşma belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="17f1a-139">Çift yönlü iletişimi yerel olarak, izin verme aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17f1a-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="17f1a-140">TCP, bunun aksine, yerel olarak çift yönlü iletişimi sağlar ve bu bağlama öğesi iletileri bir istemciye geri gönderilecek hizmeti kullanımını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="17f1a-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="17f1a-141">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="17f1a-142">Bu istemci adresi tarafından sağlanan `ClientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="17f1a-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="17f1a-143">Bu öğe türünde <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="17f1a-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="17f1a-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="17f1a-145">Eş Adı Çözümleme Protokolü (PNRP) eş ad çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="17f1a-146">Bu öğe türünde <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="17f1a-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="17f1a-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="17f1a-148">WS güvenilir Mesajlaşma ayarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="17f1a-149">Bu öğe için özel bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekleyebilir-kere teslim Güvenceleri.</span><span class="sxs-lookup"><span data-stu-id="17f1a-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="17f1a-150">Bu öğe türünde <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="17f1a-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="17f1a-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="17f1a-152">Özel bağlama güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="17f1a-153">Bu öğe türünde <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="17f1a-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="17f1a-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="17f1a-155">Bir SSL akış bağlama için güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="17f1a-156">Bu öğe türünde <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="17f1a-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="17f1a-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="17f1a-158">Bağlama tarafından kullanılacak protokolü ve işlem akışını desteklediğini belirtir `transactionProtocol` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="17f1a-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="17f1a-159">Bu öğe türünde <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="17f1a-160">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="17f1a-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="17f1a-161">Özel bağlama güvenliği akış seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="17f1a-162">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="17f1a-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17f1a-163">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="17f1a-163">Parent Elements</span></span>  
  
|<span data-ttu-id="17f1a-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="17f1a-164">Element</span></span>|<span data-ttu-id="17f1a-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17f1a-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17f1a-166">bağlamalar</span><span class="sxs-lookup"><span data-stu-id="17f1a-166">bindings</span></span>|<span data-ttu-id="17f1a-167">Windows Communication Foundation uygulamalar için tüm bağlamaları içerir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17f1a-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17f1a-168">Remarks</span></span>  
 <span data-ttu-id="17f1a-169">Özel bağlamalar WCF ileti yığın üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="17f1a-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="17f1a-170">Özel uyarlanmış bağlamaları my belirli varlıklar için yapılandırma öğeleri ekleme oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="17f1a-171">Örneğin, kullanıcı birleştirebilirsiniz `httpsTransport` bölümünde `reliableSession` bölüm ve `security` güvenilir ve güvenli bir https oluşturmak için bölüm tabanlı bağlama.</span><span class="sxs-lookup"><span data-stu-id="17f1a-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="17f1a-172">Tek bir bağlama yığında göründükleri sırada yığını öğeleri için yapılandırma öğeleri belirterek ileti yığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17f1a-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="17f1a-173">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="17f1a-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="17f1a-174">Her özel bağlama tek bir aktarım öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17f1a-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="17f1a-175">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="17f1a-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="17f1a-176">Öğeleri yığında görünme sırasını işlemleri iletiye uygulanma sırası olduğundan önemlidir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="17f1a-177">Önerilen yığını öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="17f1a-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="17f1a-178">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="17f1a-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="17f1a-179">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="17f1a-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="17f1a-180">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="17f1a-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="17f1a-181">Taşıma</span><span class="sxs-lookup"><span data-stu-id="17f1a-181">Transport</span></span>  
  
5.  <span data-ttu-id="17f1a-182">Kodlayıcı (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="17f1a-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="17f1a-183">Sistem tarafından sağlanan bağlamalar birini hizmetinizin gereksinimlerini karşılamıyor özel bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="17f1a-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="17f1a-184">Özel bağlama, örneğin, yeni bir taşıma veya bir hizmet uç noktada yeni bir kodlayıcı kullanımını etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="17f1a-185">Aşağıdakilerden birini kullanarak özel bağlama oluşturulan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> bağlama "belirli bir sırada yığılma" öğelerinin bir koleksiyondan:</span><span class="sxs-lookup"><span data-stu-id="17f1a-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="17f1a-186">En üstte bir isteğe bağlı olduğu <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> akan sağlayan işlemleri.</span><span class="sxs-lookup"><span data-stu-id="17f1a-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="17f1a-187">Sonraki isteğe bağlı olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> bir oturum ve WS-ReliableMessaging belirtiminde tanımlanan mekanizması sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="17f1a-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="17f1a-188">Bir oturum bu kavramı SOAP ve aktarım aracılar arası.</span><span class="sxs-lookup"><span data-stu-id="17f1a-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="17f1a-189">Sonraki yetkilendirme, kimlik doğrulama, koruma ve gizliliği gibi güvenlik özellikleri sağlayan bir isteğe bağlı güvenlik bağlama öğedir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="17f1a-190">Aşağıdaki güvenlik bağlama öğeleri tarafından sağlanan [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="17f1a-190">The following security binding elements are provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="17f1a-191">Sonraki isteğe bağlı ileti desenleri bağlama öğeleri tarafından belirtilir:</span><span class="sxs-lookup"><span data-stu-id="17f1a-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="17f1a-192">Sonraki isteğe bağlı aktarım yükseltmeler/Yardımcıları bağlama öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="17f1a-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="17f1a-193">Sonraki gerekli ileti kodlama bağlama öğesi var.</span><span class="sxs-lookup"><span data-stu-id="17f1a-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="17f1a-194">Kendi aktarım kullanın veya bağlamaları kodlama aşağıdaki iletiyi birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="17f1a-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="17f1a-195">Pencerenin alt gerekli aktarım öğedir.</span><span class="sxs-lookup"><span data-stu-id="17f1a-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="17f1a-196">Kendi aktarım kullanın ya da bağlama öğeleri tarafından sağlanan aktarım birini kullanın [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="17f1a-196">You can use your own transport or use one of transport binding elements provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="17f1a-197">Aşağıdaki tabloda, her katman için seçenekleri özetler.</span><span class="sxs-lookup"><span data-stu-id="17f1a-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="17f1a-198">Katman</span><span class="sxs-lookup"><span data-stu-id="17f1a-198">Layer</span></span>|<span data-ttu-id="17f1a-199">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="17f1a-199">Options</span></span>|<span data-ttu-id="17f1a-200">Gerekli</span><span class="sxs-lookup"><span data-stu-id="17f1a-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="17f1a-201">İşlem akışı</span><span class="sxs-lookup"><span data-stu-id="17f1a-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="17f1a-202">Hayır</span><span class="sxs-lookup"><span data-stu-id="17f1a-202">No</span></span>|  
|<span data-ttu-id="17f1a-203">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="17f1a-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="17f1a-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="17f1a-204">No</span></span>|  
|<span data-ttu-id="17f1a-205">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="17f1a-205">Security</span></span>|<span data-ttu-id="17f1a-206">Simetrik, asimetrik, aktarım düzeyinde</span><span class="sxs-lookup"><span data-stu-id="17f1a-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="17f1a-207">Hayır</span><span class="sxs-lookup"><span data-stu-id="17f1a-207">No</span></span>|  
|<span data-ttu-id="17f1a-208">Şeklini değiştirme</span><span class="sxs-lookup"><span data-stu-id="17f1a-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="17f1a-209">Hayır</span><span class="sxs-lookup"><span data-stu-id="17f1a-209">No</span></span>|  
|<span data-ttu-id="17f1a-210">Aktarım yükseltmeleri</span><span class="sxs-lookup"><span data-stu-id="17f1a-210">Transport Upgrades</span></span>|<span data-ttu-id="17f1a-211">SSL stream, Windows stream, eş Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="17f1a-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="17f1a-212">Hayır</span><span class="sxs-lookup"><span data-stu-id="17f1a-212">No</span></span>|  
|<span data-ttu-id="17f1a-213">Kodlama</span><span class="sxs-lookup"><span data-stu-id="17f1a-213">Encoding</span></span>|<span data-ttu-id="17f1a-214">İkili, MTOM, özel bir metin</span><span class="sxs-lookup"><span data-stu-id="17f1a-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="17f1a-215">Evet</span><span class="sxs-lookup"><span data-stu-id="17f1a-215">Yes</span></span>|  
|<span data-ttu-id="17f1a-216">Taşıma</span><span class="sxs-lookup"><span data-stu-id="17f1a-216">Transport</span></span>|<span data-ttu-id="17f1a-217">MSMQ, özel TCP ve adlandırılmış kanallar, HTTP, HTTPS özellikleri</span><span class="sxs-lookup"><span data-stu-id="17f1a-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="17f1a-218">Evet</span><span class="sxs-lookup"><span data-stu-id="17f1a-218">Yes</span></span>|  
  
 <span data-ttu-id="17f1a-219">Ayrıca, kendi bağlama öğeleri tanımlamak ve herhangi bir önceki tanımlı katmanlar arasında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="17f1a-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="17f1a-220">Sistem tarafından sağlanan bir bağlamayı değiştirmek için bağlama özel kullanma hakkında bir tartışma için bkz [nasıl yapılır: System-Provided bir bağlamayı özelleştirme](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="17f1a-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="17f1a-221">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17f1a-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="17f1a-222">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="17f1a-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="17f1a-223">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="17f1a-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="17f1a-224">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="17f1a-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="17f1a-225">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="17f1a-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="17f1a-226">customBinding öğesi</span><span class="sxs-lookup"><span data-stu-id="17f1a-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="17f1a-227">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="17f1a-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="17f1a-228">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="17f1a-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="17f1a-229">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="17f1a-229">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
