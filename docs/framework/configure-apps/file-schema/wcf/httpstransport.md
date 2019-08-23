---
title: <httpsTransport>
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: b70236e8bba93a49ca5b53538333fa63283a5f0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928531"
---
# <a name="httpstransport"></a>\<httpsTransport >
Özel bağlama için SOAP iletileri iletmek üzere bir HTTP aktarımı belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<httpsTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowCookies|İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymayacağını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özniteliği kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.|  
|authenticationScheme|HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> Bilgisi Özet kimlik doğrulamasını belirtir.<br />'Nin , Kimlik doğrulama şemasını belirleme istemcisiyle görüşür. Hem istemci hem de sunucu Kerberos 'u destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />NT NTLM kimlik doğrulamasını belirtir.<br />Basit Temel kimlik doğrulamasını belirtir.<br />Deðeri Anonim kimlik doğrulamasını belirtir.<br /><br /> Varsayılan değer anonimdir. Bu öznitelik türü <xref:System.Net.AuthenticationSchemes>. Bu öznitelik yalnızca bir kez ayarlanabilir.|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel LAN veya intranette olan yerel bir adres.<br /><br /> Hizmet adresi ile başlıyorsa Windows Communication Foundation (WCF) her zaman proxy 'yi `http://localhost`yoksayar.<br /><br /> İstemcilerin aynı makinede hizmetlerle görüşülürken bir proxy üzerinden gitmesini istiyorsanız, localhost yerine ana bilgisayar adını kullanmanız gerekir.|  
|hostnameComparisonMode|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Geçerli değerler şunlardır<br /><br /> -StrongWildcard: ("+") belirtilen şema, bağlantı noktası ve göreli URI bağlamında tüm olası ana bilgisayar adları ile eşleşir.<br />-Tam: joker karakter yok<br />-WeakWildcard: ("\*"), açıkça veya güçlü joker karakter mekanizması aracılığıyla eşleşmeyen, belirtilen şema, bağlantı noktası ve göreli UIR bağlamındaki tüm olası ana bilgisayar adı ile eşleşir.<br /><br /> Varsayılan değer Strongjoker karakterdir. Bu öznitelik türü `System.ServiceModel.HostnameComparison`.|  
|manualAddressing|Kullanıcının ileti adreslemesinin denetimini almasını sağlayan bir Boole değeri. Bu özellik genellikle yönlendirici senaryolarında kullanılır; burada uygulama, bir ileti göndermek için bir kaç hedefe sahip olduğunu belirler.<br /><br /> Olarak `true`ayarlandığında, kanal iletinin zaten giderilmiş olduğunu varsayar ve buna ek bilgi eklemez. Böylece Kullanıcı her iletiyi ayrı ayrı adresedebilir.<br /><br /> Olarak ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adres mekanizması tüm iletiler için otomatik olarak adresler oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir.<br /><br /> WCF 'in birçok bölümü arabellekleri kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|  
|maxBufferSize|Arabelleğin en büyük boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir|  
|maxReceivedMessageSize|Alınabilecek izin verilen en fazla ileti boyutunu belirten pozitif bir tamsayı. Varsayılan değer 65536 ' dir.|  
|proxyAddress|HTTP proxy adresini belirten bir URI. `useSystemWebProxy` İse`true`,buayar olmalıdır. `null` Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Kimlik doğrulaması yapılmaz.<br />Bilgisi Özet kimlik doğrulamasını belirtir.<br />'Nin , Kimlik doğrulama şemasını belirleme istemcisiyle görüşür. Hem istemci hem de sunucu Kerberos 'u destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />NT NTLM kimlik doğrulamasını belirtir.<br />Basit Temel kimlik doğrulamasını belirtir.<br />Deðeri Anonim kimlik doğrulamasını belirtir.<br /><br /> Varsayılan değer anonimdir. Bu öznitelik türü <xref:System.Net.AuthenticationSchemes>. <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> Bunun desteklenmediğini unutmayın.|  
|bölgesindeki|Proxy/sunucu üzerinde kullanılacak bölgeyi belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Sunucular, korumalı kaynakları bölümlemek için alanları kullanır. Her bölüm kendi kimlik doğrulama düzenine ve/veya yetkilendirme veritabanına sahip olabilir. Bölgeler yalnızca temel ve Özet kimlik doğrulaması için kullanılır. İstemci başarıyla kimlik doğrulamasından geçtikten sonra, kimlik doğrulaması belirli bir bölgedeki tüm kaynaklar için geçerli olur. Bölge ayrıntılı açıklaması için, [IETF Web SITESINDE](https://www.ietf.org)rfc 2617 ' a bakın.|  
|requireClientCertificate|Sunucunun HTTPS el sıkışmasının bir parçası olarak istemci sertifikası sağlamasını gerektirip gerektirmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|transferMode|İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirtir. Geçerli değerler şunlardır:<br /><br /> Alınıp İstek ve yanıt iletilerinin ara belleğe alınır.<br />Akan İstek ve yanıt iletileri akışlardır.<br />-StreamedRequest: İstek iletisi akışla gönderilir ve yanıt iletisi arabelleğe kaydedilir.<br />-Streammedresponse: İstek iletisi arabelleğe alındı ve yanıt iletisi akışla.<br /><br /> Varsayılan değer arabelleğe alındı. Bu öznitelik türü <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Sunucuda güvensiz bağlantı paylaşımının etkin olup olmadığını belirten bir Boolean değer. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısında bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Kullanıcıya özel ayarlar yerine makine genelindeki proxy ayarlarının kullanılıp kullanılmayacağını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpsTransport` Öğesi, HTTPS taşıma protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır. HTTPS, güvenli birlikte çalışabilirlik amaçları için kullanılan birincil aktarımdır. HTTPS, diğer Web Hizmetleri yığınlarıyla birlikte çalışabilirliği sağlamak için Windows Communication Foundation (WCF) tarafından desteklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
