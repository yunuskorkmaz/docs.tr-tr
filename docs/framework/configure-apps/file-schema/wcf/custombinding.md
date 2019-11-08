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
# <a name="custombinding"></a>\<customBinding >

Kullanıcı için mesajlaşma yığını üzerinde tam denetim sağlar.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customBinding >**  

## <a name="syntax"></a>Sözdizimi

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

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|closeTimeout|Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|
|name|Bağlamanın yapılandırma adını içeren bir dize. Bu değer, özel bağlama için kimlik dizesi görevi gören Kullanıcı tanımlı bir dizedir. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|
|openTimeout|Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|
|receiveTimeout|Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|
|Binding üstündeki SendTimeout|Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<compositeDuplex >](compositeduplex.md)|Özel bağlamaya iki yönlü mesajlaşma belirtir. Çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır. Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.<br /><br /> İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır. Bu istemci adresi `ClientBaseAddress` özniteliği tarafından sağlanır.<br /><br /> Bu öğe <xref:System.ServiceModel.Configuration.CompositeDuplexElement>türündedir.|
|[\<pnrpPeerResolver >](pnrppeerresolver.md)|Eş adı çözümleme Protokolü (PNRP) eş adı çözümleyicisini belirtir. Bu öğe <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>türündedir.|
|[Reliableoturum > \<](reliablesession.md)|WS-güvenilir mesajlaşma için ayarı belirtir. Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir. Bu öğe <xref:System.ServiceModel.Configuration.ReliableSessionElement>türündedir.|
|[\<Güvenlik >](security-of-custombinding.md)|Özel bağlamanın güvenliği için seçenekleri belirtir. Bu öğe <xref:System.ServiceModel.Configuration.SecurityElement>türündedir.|
|[\<sslStreamSecurity >](sslstreamsecurity.md)|SSL akışı bağlamasının güvenlik ayarlarını belirtir. Bu öğe <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>türündedir.|
|[\<transactionFlow >](transactionflow.md)|Bağlamanın işlem akışını ve `transactionProtocol` özniteliği tarafından kullanılacak protokolü desteklediğini belirtir. Bu öğe <xref:System.ServiceModel.Configuration.TransactionFlowElement>türündedir.|
|[windowsStreamSecurity > \<](windowsstreamsecurity.md)|Özel bağlamanın akış güvenliğini sağlama seçeneklerini belirtir. Bu öğe <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>türündedir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|bağlamalar|Windows Communication Foundation uygulamaların tüm bağlamalarını içerir.|

## <a name="remarks"></a>Açıklamalar

Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar. Özel uyarlanmış bağlamalar, belirli varlıklar için yapılandırma öğelerini eklemem oluşturulabilir. Örneğin, Kullanıcı, güvenilir ve güvenli bir https tabanlı bağlama oluşturmak için `httpsTransport` bölümünü, `reliableSession` bölümünü ve `security` bölümünü birleştirebilirler.

Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar. Her öğe, yığının bir öğesini tanımlar ve yapılandırır. Her özel bağlamada bir ve yalnızca bir Transport öğesi olmalıdır. Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.

Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek? Yığın öğelerinin önerilen sırası aşağıda verilmiştir:

1. İşlemler (isteğe bağlı)

2. Güvenilir Mesajlaşma (isteğe bağlı)

3. Güvenlik (isteğe bağlı)

4. Aktarım

5. Kodlayıcı (isteğe bağlı)

Sistem tarafından belirtilen bağlamalardan biri hizmetinizin gereksinimlerini karşılamadığında özel bir bağlama kullanın. Bir hizmet uç noktasında yeni bir taşımanın veya yeni bir kodlayıcının kullanımını etkinleştirmek için, örneğin, özel bir bağlama kullanılabilir.

Özel bir bağlama, belirli bir sırada "yığılmış" olan bağlama öğeleri koleksiyonundan <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> biri kullanılarak oluşturulur:

- En üstte, akan işlemlere izin veren isteğe bağlı bir <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>.

- Next, WS-ReliableMessaging belirtiminde tanımlanan bir oturum ve sıralama mekanizması sağlayan isteğe bağlı bir <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>. Bu oturum kavramı, SOAP ve aktarım aracıları arasında geçiş yapabilir.

- Daha sonra yetkilendirme, kimlik doğrulama, koruma ve gizlilik gibi güvenlik özellikleri sağlayan isteğe bağlı bir güvenlik bağlama öğesidir. Aşağıdaki güvenlik bağlama öğeleri Windows Communication Foundation (WCF) tarafından sağlanır:

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- Daha sonra bağlama öğeleri tarafından belirtilen isteğe bağlı ileti desenleri şunlardır:

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- Daha sonra isteğe bağlı taşıma yükseltmeleri/yardımcıları bağlama öğeleri şunlardır:

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- Next, gerekli bir ileti kodlama bağlama öğesidir. Kendi taşıyıcıyı kullanabilir veya aşağıdaki ileti kodlama bağlamalarından birini kullanabilirsiniz:

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- En altta gerekli bir taşıma öğesidir. Kendi taşıyıcıyı kullanabilir veya Windows Communication Foundation (WCF) tarafından sunulan taşıma bağlama öğelerinden birini kullanabilirsiniz:

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

Aşağıdaki tabloda her bir katmanın seçenekleri özetlenmektedir.

|Katmanı|Seçenekler|Gerekli|
|-----------|-------------|--------------|
|İşlem akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|Hayır|
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|Hayır|
|Güvenlik|Simetrik, asimetrik, aktarım düzeyi|Hayır|
|Şekil değişikliği|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|Hayır|
|Aktarım yükseltmeleri|SSL akışı, Windows Stream, eş çözümleyici|Hayır|
|Şifreleme|Metin, Ikili, MTOM, özel|Evet|
|Aktarım|TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel|Evet|

Ayrıca, kendi bağlama öğelerinizi tanımlayabilir ve bunları önceki tanımlı katmanlardan herhangi biri arasına ekleyebilirsiniz.

Sistem tarafından sağlanmış bir bağlamayı değiştirmek için özel bağlama kullanma hakkında tartışma için bkz. [nasıl yapılır: sistem tarafından belirtilen bağlamayı özelleştirme](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\< bağlama >](bindings.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [customBinding öğesi](custombinding.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
