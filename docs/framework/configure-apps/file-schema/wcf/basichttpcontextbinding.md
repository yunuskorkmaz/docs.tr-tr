---
title: '&lt;basicHttpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 39b16b82-4ec6-4eff-8031-67e026870961
ms.openlocfilehash: fb6388244ea0bfb583c9a0d3ee5a4843727e45a0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753098"
---
# <a name="ltbasichttpcontextbindinggt"></a>&lt;basicHttpContextBinding&gt;
Bağlam için sağlayan bir bağlama belirtme <xref:System.ServiceModel.BasicHttpBinding> exchange mekanizması olarak HTTP tanımlama bilgilerini sağlayarak değiştirilmek üzere.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<basicHttpContextBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<basicHttpContextBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
       name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                                    clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</basicHttpContextBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`allowCookies`|İstemci tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullan ASMX Web Hizmetleri ile etkileşim kurarken, bu özelliği kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalandığından emin olabilir.|  
|`bypassProxyOnLocal`|Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel bir adres varsa, yerel bir Internet kaynaktır. Yerel bir adres aynı bilgisayarda, yerel LAN veya intranet ve, sözdizimsel olarak, URI'ler olduğu gibi bir nokta (.) eksikliği tarafından tanımlanan biridir "http://webserver/"ve"http://localhost/".<br /><br /> Bu öznitelik ayarlama BasicHttpBinding ile yapılandırılmış uç noktaları yerel kaynaklara erişirken proxy sunucusu kullanıp kullanmayacağınızı belirler. Bu öznitelik değilse `true`, yerel Internet kaynakların isteklerine proxy sunucusunu kullanmaz. Bu öznitelik ayarlandığında hizmetler için aynı makinede konuşurken bir proxy üzerinden gitmek için istemcilerin istiyorsanız konak adı (localhost yerine) kullanın `true`.<br /><br /> Bu öznitelik olduğunda `false`, proxy sunucu üzerinden yapılan tüm Internet istekleri.|  
|`closeTimeout`|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`envelopeVersion`|Bu bağlama tarafından işlenen iletiler için kullanılan SOAP sürümünü belirtir. Soap11 yalnızca geçerli değeridir.|  
|`hostnameComparisonMode`|URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Bu öznitelik türünde <xref:System.ServiceModel.HostNameComparisonMode>, ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirtir. Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, eşleşme ana bilgisayar adı yok sayar.|  
|`maxBufferPoolSize`|Kanaldan iletiler alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak için ayrılan bellek miktarını belirten bir tamsayı değeri. Varsayılan değer 524288 (0x80000): bayt sayısı.<br /><br /> Arabellek Yöneticisi arabellek havuzu kullanarak arabellekleri kullanma maliyetini en aza indirir. Kanal dışında geldiğinizde arabellekleri hizmeti tarafından iletilerini işlemek için gereklidir. İleti yükü işlemek için arabellek havuzunda yeterli bellek yoksa, arabellek Yöneticisi atık toplama yükünü artırır CLR yığınından ek bellek ayırmanız gerekir. CLR çöp yığınına gelen kapsamlı ayırma arabellek havuzu boyutu çok küçük olduğunu ve bu özniteliği tarafından belirtilen sınırı artırarak performansı ile daha büyük bir ayırma geliştirilebilir göstergesidir.|  
|`maxBufferSize`|Bu bağlama ile yapılandırılan bir uç nokta için işlenirken iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirtir bir tamsayı değeri. Varsayılan değer 65.536 bayttır.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılan kanalda alınan bir ileti için üstbilgileri dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı. İleti alıcı için çok büyük ise gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. Varsayılan 65.536 bayt'tır.|  
|`messageEncoding`|SOAP iletisi kodlanması için kullanılan Kodlayıcı tanımlar. Geçerli değerler şunlardır:<br /><br /> -Metin: metin ileti Kodlayıcı kullanın.<br />-Mtom: bir ileti iletim kuruluş mekanizması 1.0 (MTOM) Kodlayıcısı kullanın.<br /><br /> Varsayılan metindir. Bu öznitelik türünde <xref:System.ServiceModel.WSMessageEncoding>.|  
|`messageVersion`|İstemciler ve bağlama ile yapılandırılan hizmetler tarafından kullanılan iletisi sürümünü belirtir. Bu öznitelik türünde <xref:System.ServiceModel.Channels.MessageVersion>.|  
|`name`|Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın. Ayrıca, bu ad aynı türde bağlamaları arasında benzersizdir. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|XML ad alanı bağlamanın belirtir. Varsayılan değer "http://tempuri.org/Bindings". Her bağlama sahip bir `name` ve `namespace` birlikte benzersiz olarak özniteliği hizmet meta verilerde tanımlayın.|  
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`proxyAddress`|HTTP proxy adresini içeren bir URI. Varsa `useSystemWebProxy` ayarlanır `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|`receiveTimeout`|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10: 00'dır.|  
|`sendTimeout`|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`textEncoding`|Karakter kümesi bağlama iletilerde yayma için kullanılacak kodlama ayarlar. Geçerli değerler şunlardır:<br /><br /> -BigEndianUnicode: Unicode BigEndian kodlama.<br />-Unicode: 16 bit kodlama.<br />-UTF8: 8 bit kodlama<br /><br /> UTF8 varsayılandır. Bu öznitelik türünde <xref:System.Text.Encoding>.|  
|`transferMode`|Geçerli bir <xref:System.ServiceModel.TransferMode> iletilerin ara belleğe veya bir istek veya yanıt akışı belirten değer.|  
|`useDefaultWebProxy`|Otomatik yapılandırılan HTTP Proxy'si sisteminin kullanılması gerekip gerekmediğini, varsa belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama öğesi değişimi mekanizması bağlamı için bir parçası olarak ve bir koruma düzeyi sağlar bir `BasicHttpBinding`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.BasicHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)  
 [\<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
