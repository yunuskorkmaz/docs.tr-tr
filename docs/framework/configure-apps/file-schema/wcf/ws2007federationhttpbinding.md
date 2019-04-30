---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: e6215465acbf9bb94298d282d15f8735a0e20c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673088"
---
# <a name="ws2007federationhttpbinding"></a>\<ws2007FederationHttpBinding >

Türetilen bir güvenli ve birlikte çalışabilen bağlama [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve birleşik güvenliği destekler.

```xml
<system.ServiceModel>
  <bindings>
    <ws2007FederationHttpBinding>
```

## <a name="syntax"></a>Sözdizimi

```xml
<ws2007FederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
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
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`bypassProxyOnLocal`|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir değer. Varsayılan, `false` değeridir.|
|`closeTimeout`|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|
|`hostNameComparisonMode`|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, ana bilgisayar adı eşleşme yok sayar.|
|`maxBufferPoolSize`|Bu bağlama için en fazla arabellek havuzu boyutu. 524.288 bayt (512 * 1024) varsayılandır. Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutu. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|
|`messageEncoding`|İletisini kodlamak için kullanılan kodlayıcıya tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metni: Bir metin ileti Kodlayıcı kullanın.<br />-Mtom: İleti Aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.<br /><br /> Metin varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.|
|`name`|Bağlama yapılandırma adı. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|
|`privacyNoticeAt`|Gizlilik bildirimini bulunduğu bir URI.|
|`privacyNoticeVersion`|Geçerli gizlilik bildirimini sürümü.|
|`proxyAddress`|HTTP proxy adresini belirten bir URI. Varsa `useDefaultWebProxy` olduğu `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|
|`receiveTimeout`|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|
|`sendTimeout`|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|
|`textEncoding`|İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar. Geçerli değerler şunlardır:<br /><br /> -   BigEndianUnicode: Unicode büyük Endian kodlaması.<br />-Unicode: 16-bit kodlaması.<br />-   UTF8: 8-bit kodlaması.<br /><br /> UTF8 varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|
|`transactionFlow`|WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir değeri. Varsayılan, `false` değeridir.|
|`useDefaultWebProxy`|Sistemin otomatik yapılandırılan HTTP Ara sunucusu kullanılıp kullanılmayacağını belirten bir değer. Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlı değil) Bu öznitelik ise `true`. Varsayılan, `true` değeridir.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Güvenilir oturumlar kanal uç noktaları arasında kurulan olup olmadığını belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|

## <a name="remarks"></a>Açıklamalar

Federasyon kimlikleri birden fazla kuruluşlar veya kimlik doğrulama ve yetkilendirme için güven etki alanları arasında paylaşmak için yeteneğidir. Bir güven etki alanı kimlik gösterimden diğerine eşlemek için WS-Trust protokolü kullanır. Karma mod güvenliği yanı sıra SOAP Güvenliği Federasyon HTTP bağlama destekler, ancak aktarım güvenliği desteklemez. Bu bağlama ile yapılandırılan hizmetler, HTTP aktarımı kullanmanız gerekir. Daha fazla bilgi için [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).

## <a name="example"></a>Örnek

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
