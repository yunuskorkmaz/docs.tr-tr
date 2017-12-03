---
title: '&lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6af846937556968067d89a279e595374cce99ae4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt;
Doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<ws2007HttpBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowCookies`|İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar olup olmadığını belirten bir değer. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullanan ASP.NET Web Hizmetleri ile (ASMX) etkileşim kurarken, bu özelliği kullanabilirsiniz. Bu, sunucunun döndürür tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalanır sağlar.|  
|`bypassProxyOnLocal`|Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir değer. Varsayılan, `false` değeridir.|  
|`closeTimeout`|A <xref:System.TimeSpan> tamamlamak bir kapatma işlemi için zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`hostnameComparisonMode`|Tekdüzen Kaynak Tanımlayıcıları (URI'ler) ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutu. Varsayılan 524.288 (512 × 1024) bayttır. Birçok bölümlerini [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] arabellekleri kullanın. Çöp toplama arabellekleri için olduğu gibi oluşturma ve her defa arabellek yok etme, pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve işiniz bittiğinde havuza geri dönemez. Oluşturma ve yok etme arabellekleri yükünü önler.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılan bir kanal alabilir üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır.|  
|`messageEncoding`|İleti kodlanması için kullanılan Kodlayıcı tanımlar. Geçerli değerler şunlardır:<br /><br /> -   `Text`: Bir metin ileti Kodlayıcı kullanın.<br />-   `Mtom`: Bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.<br /><br /> Varsayılan, `Text` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Bağlama yapılandırma adı. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`proxyAddress`|HTTP proxy adresini belirtir URI. Varsa `useSystemWebProxy` olan `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|`receiveTimeout`|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`sendTimeout`|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`textEncoding`|Karakter bağlama verme iletileri için kullanılacak kodlama kümesini belirtir. Geçerli değerler şunlardır:<br /><br /> -   `UnicodeFffeTextEncoding`: Unicode Big Endian kodlama.<br />-   `Utf16TextEncoding`: 16 bit kodlama.<br />-   `Utf8TextEncoding`: 8 bit kodlama.<br /><br /> Varsayılan, `Utf8TextEncoding` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.Text.Encoding>.|  
|`transactionFlow`|Bağlama boyunca WS-işlemleri destekleyip desteklemediğini belirten bir değer. Varsayılan, `false` değeridir.|  
|`useDefaultWebProxy`|Sistemin otomatik yapılandırılan HTTP Proxy'si kullanılıp kullanılmayacağını belirten değer. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları işleyebilir SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Güvenilir oturumlar kanal uç noktaları arasında kurulan olup olmadığını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `WS2007HttpBinding` Bir sistem tarafından sağlanan bir bağlamayı benzer ekler `WSHttpBinding` ancak kuruluş terfi, yapılandırılmış bilgi standartları (OASIS) standart sürümleri ReliableSession, güvenlik ve TransactionFlow protokollerini kullanır. Nesne modeli veya varsayılan ayarlarını herhangi bir değişiklik, bu bağlama kullanılırken gereklidir.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
