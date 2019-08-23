---
title: <httpTransport>
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 2d651101b720d427391274d0e02690588123cd53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925517"
---
# <a name="httptransport"></a>\<httpTransport >
Özel bağlama için SOAP iletileri iletmek üzere bir HTTP aktarımı belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<httpTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpTransport allowCookies="Boolean"
               authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
               bypassProxyOnLocal="Boolean"
               hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
               keepAliveEnabled="Boolean"
               maxBufferSize="Integer"
               proxyAddress="Uri"
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
               realm="String"
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
|hostnameComparisonMode|URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Geçerli değerler şunlardır<br /><br /> -StrongWildcard: ("+") belirtilen şema, bağlantı noktası ve göreli URI bağlamında tüm olası ana bilgisayar adları ile eşleşir.<br />-Tam: joker karakter yok<br />-WeakWildcard: ("\*"), açıkça veya güçlü joker karakter mekanizması aracılığıyla eşleşmeyen, belirtilen şema, bağlantı noktası ve göreli UIR bağlamındaki tüm olası ana bilgisayar adı ile eşleşir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.HostNameComparisonMode>. Varsayılan, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> değeridir.|  
|keepAliveEnabled|Internet kaynağına kalıcı bir bağlantı yapılıp yapılmayacağını belirten Boolean bir değer.|  
|maxBufferSize|Arabelleğin en büyük boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir|  
|proxyAddress|HTTP proxy adresini belirten bir URI. `useSystemWebProxy` İse`true`,buayar olmalıdır. `null` Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Kimlik doğrulaması yapılmaz.<br />Bilgisi Özet kimlik doğrulamasını belirtir.<br />'Nin , Kimlik doğrulama şemasını belirleme istemcisiyle görüşür. Hem istemci hem de sunucu Kerberos 'u destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />NT NTLM kimlik doğrulamasını belirtir.<br />Basit Temel kimlik doğrulamasını belirtir.<br />Deðeri Anonim kimlik doğrulamasını belirtir.<br /><br /> Varsayılan değer anonimdir. Bu öznitelik türü <xref:System.Net.AuthenticationSchemes>. <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> Bunun desteklenmediğini unutmayın.|  
|bölgesindeki|Proxy/sunucu üzerinde kullanılacak bölgeyi belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Sunucular, korumalı kaynakları bölümlemek için alanları kullanır. Her bölüm kendi kimlik doğrulama düzenine ve/veya yetkilendirme veritabanına sahip olabilir. Bölgeler yalnızca temel ve Özet kimlik doğrulaması için kullanılır. İstemci başarıyla kimlik doğrulamasından geçtikten sonra, kimlik doğrulaması belirli bir bölgedeki tüm kaynaklar için geçerli olur. Bölge ayrıntılı açıklaması için, [IETF Web SITESINDE](https://www.ietf.org)rfc 2617 ' a bakın.|  
|transferMode|İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirtir. Geçerli değerler şunlardır:<br /><br /> Alınıp İstek ve yanıt iletilerinin ara belleğe alınır.<br />Akan İstek ve yanıt iletileri akışlardır.<br />-StreamedRequest: İstek iletisi akışla gönderilir ve yanıt iletisi arabelleğe kaydedilir.<br />-Streammedresponse: İstek iletisi arabelleğe alındı ve yanıt iletisi akışla.<br /><br /> Varsayılan değer arabelleğe alındı. Bu öznitelik türü <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Sunucuda güvensiz bağlantı paylaşımının etkin olup olmadığını belirten bir Boolean değer. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısında bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Kullanıcıya özel ayarlar yerine makine genelindeki proxy ayarlarının kullanılıp kullanılmayacağını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpTransport` Öğesi, HTTP aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır. HTTP, birlikte çalışabilirlik amacıyla kullanılan birincil aktarımdır. Bu taşıma, diğer WCF olmayan Web Hizmetleri yığınlarıyla birlikte çalışabilirliği sağlamak için Windows Communication Foundation (WCF) tarafından desteklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HttpTransportElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
