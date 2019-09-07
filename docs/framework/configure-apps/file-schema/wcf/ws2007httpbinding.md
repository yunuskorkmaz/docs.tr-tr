---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 0f0dc3ebe34ea45c1b464ff4fe437694ff4761f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399055"
---
# <a name="ws2007httpbinding"></a>\<ws2007HttpBinding>
<xref:System.ServiceModel.WSHttpBinding.Security%2A> ,<xref:System.ServiceModel.ReliableSession>, Ve<xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğelerinin doğru sürümleri için destek sağlayan bir birlikte çalışabilen bağlama tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
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
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowCookies`|İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir değer. Varsayılan, `false` değeridir.<br /><br /> Bu özelliği, tanımlama bilgilerini kullanan ASP.NET Web Hizmetleri (ASMX) ile etkileşim kurarken kullanabilirsiniz. Bu, sunucunun döndürdüğü tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalanmasını sağlar.|  
|`bypassProxyOnLocal`|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer. Varsayılan, `false` değeridir.|  
|`closeTimeout`|Bir <xref:System.TimeSpan> Close işleminin tamamlanacağı zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`hostNameComparisonMode`|Tekdüzen Kaynak tanımlayıcılarını (URI) ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Bu öznitelik, ana bilgisayar <xref:System.ServiceModel.HostNameComparisonMode>adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşenlerin ana bilgisayar adını yok saymaz.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutu. Varsayılan değer 524.288 bayttır (512 × 1.024). Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır. Arabellekler için çöp toplama gibi, her kullanıldıkları sırada arabellekleri oluşturma ve yok etme işlemleri pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu, arabellekleri oluşturma ve yok etme içindeki ek yükü önler.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılan bir kanalın alabileceği üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|  
|`messageEncoding`|İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar. Geçerli değerler şunlardır:<br /><br /> -   `Text`: Bir SMS mesajı Kodlayıcısı kullanın.<br />-   `Mtom`: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.<br /><br /> Varsayılan, `Text` değeridir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Bağlamanın yapılandırma adı. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`proxyAddress`|HTTP proxy adresini belirten bir URI. `useSystemWebProxy` İse`true`,buayar olmalıdır. `null` Varsayılan, `null` değeridir.|  
|`receiveTimeout`|Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`sendTimeout`|Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`textEncoding`|Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlamasını belirtir. Geçerli değerler şunlardır:<br /><br /> -   `UnicodeFffeTextEncoding`: Unicode Big endian kodlaması.<br />-   `Utf16TextEncoding`: 16 bit kodlama.<br />-   `Utf8TextEncoding`: 8 bit kodlama.<br /><br /> Varsayılan, `Utf8TextEncoding` değeridir.<br /><br /> Bu öznitelik türü <xref:System.Text.Encoding>.|  
|`transactionFlow`|Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer. Varsayılan, `false` değeridir.|  
|`useDefaultWebProxy`|Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir değer. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-wshttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan bitiş noktaları tarafından kullanılabilen SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Reliableoturum >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 , `WS2007HttpBinding` ' A `WSHttpBinding` benzer bir sistem tarafından sağlanmış bir bağlama ekler, ancak bu, bir kuruluştan, reliableoturum, güvenlik ve TransactionFlow protokollerinin yapılandırılmış bilgi standartları (Oasa) standart sürümlerini kullanır. Bu bağlama kullanılırken nesne modelinde veya varsayılan ayarlarda değişiklik yapılması gerekmez.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
