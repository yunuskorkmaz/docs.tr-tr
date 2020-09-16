---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: a57b5ff0b4a8186ffc4c01b5e0824100f265551c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557287"
---
# \<wsFederationHttpBinding>

WS-Federation destekleyen bir bağlama tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**  

## <a name="syntax"></a>Syntax

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

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.|
|closeTimeout|<xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|
|hostnameComparisonMode|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür. Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.|
|maxBufferPoolSize|Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı. Varsayılan değer 524.288 bayttır (512 * 1024). Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|
|Değerini|Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|
|messageEncoding|İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: bir metin mesajı Kodlayıcısı kullanın.<br />-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.<br /><br /> Varsayılan değer metindir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding> .|
|name|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. .NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|
|openTimeout|Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|
|privacyNoticeAt|Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.|
|privacyNoticeVersion|Geçerli gizlilik bildiriminin sürümünü belirten bir tamsayı.|
|proxyAddress|HTTP proxy adresini belirten bir URI. `useDefaultWebProxy`İse `true` , bu ayar olmalıdır `null` . Varsayılan değer: `null`.|
|receiveTimeout|<xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:10:00 ' dir.|
|Binding üstündeki SendTimeout|<xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> . Varsayılan değer 00:01:00 ' dir.|
|Kodkodu kodlama|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -Bigendianunıcode: Unicode Bigenyen kodlaması.<br />-UNICODE: 16 bit kodlama.<br />-UTF8:8 bit kodlama<br /><br /> Varsayılan değer UTF8 ' dir. Bu öznitelik türü <xref:System.Text.Encoding> ..|
|transactionFlow|Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan değer: `false`.|
|useDefaultWebProxy|Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir Boole değeri. Bu öznitelik ise, ara sunucu adresi `null` (ayarlı değil) olmalıdır `true` . Varsayılan değer: `true`.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> .|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<bindings>](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|

## <a name="remarks"></a>Açıklamalar

Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla sistem genelinde kimlik paylaşma olanağıdır. Bu kimlikler, kullanıcılara veya makinelere başvurabilir. Federasyon HTTP, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini kullanarak özel olarak desteklenmez. Bu bağlama WS-Federation protokolü için Windows Communication Foundation (WCF) desteği sağlar. Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.

Bağlamalar bağlama öğelerinden oluşan bir yığından oluşur. İçindeki bağlama öğelerinin yığını

`wsFederationHttpBinding` , içinde bulunan ile aynıdır `wsHttpBinding`

ne zaman [\<security>](security-of-wsfederationhttpbinding.md) varsayılan değerine ayarlanır <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> .

, `wsFederationHttpBinding` ' Deki ileti güvenliği ayarlarının ayrıntılarını denetler [\<message>](message-element-of-wsfederationhttpbinding.md) . [\<security>](security-of-wsfederationhttpbinding.md)Öğesi, bağlama oluşturulduktan sonra bağlama tarafından kullanılan güvenlik değiştirilemez olarak yalnızca erişim sunmadığını unutmayın.

`wsFederationHttpBinding`Ayrıca, gizlilik bildiriminin bulunduğu URI 'yi ayarlamak ve almak için bir privacyNoticeAt özniteliği sağlar.

İlkenin güvenli tutulması, Federasyon senaryolarında özellikle önemlidir. Bu öneri, ilkeyi kötü amaçlı kullanıcılardan korumak için HTTPS gibi bir güvenlik biçimi kullanmaktır.

Bu bağlamayı kullanan Federasyon senaryolarında, hizmet ilkesi potansiyel olarak, verilen (SAML) belirtecini şifrelemek için kullanılan anahtar, belirtece yerleştirilecek talepler türü ve benzeri önemli bilgilere sahiptir. Bu ilke ile oynanabilir bir saldırgan, verilen belirtecin anahtarını daha fazla değişiklik, bilgi açığa çıkması ve diğer kötü amaçlı davranışa göre bulabilir. Bunu önlemeye yardımcı olmak için, ilkenin hizmetten güvenli bir şekilde (örneğin, HTTPS kullanılarak) alınması gerekir.

Bu bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).

## <a name="example"></a>Örnek

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
