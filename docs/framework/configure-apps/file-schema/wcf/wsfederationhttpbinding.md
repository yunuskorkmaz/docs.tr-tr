---
title: '&lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 943887dd2bf3b309c0663a9eb06e658ee5957844
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365825"
---
# <a name="ltwsfederationhttpbindinggt"></a>&lt;wsFederationHttpBinding&gt;
WS-Federation destekleyen bir bağlama tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
wsFederationBinding öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
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
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
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
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|hostnameComparisonMode|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, ana bilgisayar adı eşleşme yok sayar.|  
|maxBufferPoolSize|Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı. 524.288 bayt (512 * 1024) varsayılandır. Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|maxReceivedMessageSize|Bu bağlama ile yapılandırılan bir kanalda alınabilecek üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|  
|messageEncoding|İletisini kodlamak için kullanılan kodlayıcıya tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: metin ileti Kodlayıcı kullanın.<br />-Mtom: ileti aktarım kuruluş mekanizması 1.0 (MTOM) encoder'ı kullanın.<br /><br /> Metin varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Bağlama yapılandırma adını içeren bir dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|opentimeout =|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|privactyNoticeAt|Gizlilik bildirimini bulunduğu bir URI öğesini belirten bir dize.|  
|privactyNoticeVersion|Geçerli gizlilik bildirimini sürümünü belirten bir tamsayı.|  
|proxyAddress|HTTP proxy adresini belirten bir URI. Varsa `useDefaultWebProxy` olduğu `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|receiveTimeout|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|  
|SendTimeout|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|textEncoding|İletileri bağlamadaki yayma için kullanılacak kodlama karakter kümesini ayarlar. Geçerli değerler şunlardır:<br /><br /> -BigEndianUnicode: Unicode kodlama BigEndian.<br />-Unicode: 16-bit kodlaması.<br />-UTF8: 8-bit kodlama<br /><br /> UTF8 varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>...|  
|transactionFlow|WS işlem akışı sağlama bağlama destekleyip desteklemediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|useDefaultWebProxy|Sistemin otomatik yapılandırılan HTTP Ara sunucusu kullanılıp kullanılmadığını gösteren bir Boole değeri. Proxy adresi olmalıdır `null` (diğer bir deyişle, ayarlı değil) Bu öznitelik ise `true`. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar bir kanal uç noktaları arasında yapıldığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Federasyon kimlikleri kimlik doğrulaması ve yetkilendirme için birden çok sistemleri arasında paylaşmak için yeteneğidir. Bu kimlik, kullanıcılar veya makinelerin başvurabilir. Karma mod güvenliği yanı sıra SOAP Güvenliği Federasyon HTTP destekler ancak yalnızca Aktarım güvenliği kullanmayı desteklemez. Bu bağlama için WS-Federation protokolü Windows Communication Foundation (WCF) desteği sağlar. Bu bağlama ile yapılandırılan hizmetler, HTTP aktarımı kullanmanız gerekir.  
  
 Bağlamaları bağlama öğelerinin yığınını oluşur. Yığın öğeleri bağlama  
  
 `wsFederationHttpBinding` bulunan aynı `wsHttpBinding`  
  
 zaman [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) varsayılan değerine ayarlanır <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.  
  
 `wsFederationHttpBinding` İleti güvenlik ayarlarının ayrıntılarını kontrol [ \<ileti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md). Unutmayın [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) öğesi bağlama oluşturulduktan sonra yalnızca bağlama tarafından kullanılan güvenlik değiştirilemez olarak get erişim sağlar.  
  
 `wsFederationHttpBinding` Gizlilik bildirimini bulunduğu URI almak ve ayarlamak için bir privactyNoticeAt özniteliği de sağlar.  
  
 İlke güvende tutmanın, Federasyon senaryolarında özellikle önemlidir. İlke kötü amaçlı kullanıcılara karşı korumak için güvenlik, HTTPS gibi biçimi kullanmak için önerilir.  
  
 Bu bağlama kullanarak Federasyon senaryolarında hizmet ilkesi potansiyel olarak verilen (SAML) belirteç, belirteçte yerleştirin vb. için talep türünü şifrelemek için kullanılacak anahtarı gibi önemli bilgiler vardır. Bu ilke değiştirilmiş, bir saldırganın başka oynama, bilgi ifşası ve diğer kötü amaçlı davranışları için önde gelen verilen belirteç anahtarı keşfedin. Bunu önlemek için ilke (HTTPS kullanan güvenli bir şekilde örneğin) hizmetinden alınmalıdır.  
  
 Bu bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
