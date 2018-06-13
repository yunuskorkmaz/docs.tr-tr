---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 77400348e9adc31d8121fc75f46d75d757af270f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362879"
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
SOAP iletilerine özel bağlama için iletmek için bir HTTP taşıması belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<httpTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
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
|allowCookies|İstemcinin tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullan ASMX Web Hizmetleri ile etkileşim kurarken, bu öznitelik kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalandığından emin olabilir.|  
|authenticationScheme|Bir HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılacak protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Özeti: Özet kimlik doğrulaması belirtir.<br />-Anlaş: kimlik doğrulama düzenini belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulamasını belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>. Bu öznitelik yalnızca bir kez ayarlanabilir.|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel bir adres yerel LAN ya da intranet biridir.<br /><br /> Windows Communication Foundation (WCF) hizmeti adresi ile başlıyorsa proxy her zaman yoksayar http://localhost.<br /><br /> İstemcileri bir proxy üzerinden hizmetler için aynı makinede konuşurken gitmek için isterseniz localhost yerine ana bilgisayar adı kullanmanız gerekir.|  
|hostnameComparisonMode|URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Geçerli değerler,<br /><br /> -StrongWildcard: ("+") belirtilen şema, bağlantı noktası ve göreli URI bağlamında tüm olası ana bilgisayar adı ile eşleşir.<br />-Tam: joker<br />-WeakWildcard: ("*") bağlamında belirtilen düzenini, bağlantı noktası ve açıkça eşlenen olmayan göreli UIR ya da güçlü joker mekanizması aracılığıyla olası tüm ana bilgisayar adı ile eşleşir.<br /><br /> StrongWildcard varsayılandır. Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`.|  
|keepAliveEnabled|Internet kaynağıyla kalıcı bir bağlantı görüntüleyip görüntülemeyeceğini belirten bir Boole değeri.|  
|maxBufferSize|Arabelleğin en büyük boyutu belirtir pozitif bir tamsayı. 524288 varsayılandır|  
|proxyAddress|HTTP proxy adresini belirtir URI. Varsa `useSystemWebProxy` olan `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|Bir HTTP proxy'si tarafından işlenen istemci isteklerinin kimlik doğrulaması için kullanılacak protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Kimlik doğrulaması gerçekleştirilmez.<br />-Özeti: Özet kimlik doğrulaması belirtir.<br />-Anlaş: kimlik doğrulama düzenini belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulamasını belirtir.<br />-IntegratedWindowsAuthentication: Windows kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>.|  
|Bölge|Proxy/sunucuda kullanmak için bölge belirten bir dize. Varsayılan boş bir dizedir.<br /><br /> Sunucuları, korunan kaynaklara bölümlemek için bölgeleri kullanır. Her bölüm kendi kimlik doğrulama düzeni ve/veya yetkilendirme veritabanına sahip olabilir. Bölge için basic kullanılır ve Özet kimlik doğrulaması. Bir istemci kimliğini başarıyla doğrulayan sonra kimlik doğrulama, belirli bir bölgedeki tüm kaynaklar için geçerlidir. RFC 2617 adresindeki bölgeler ayrıntılı bir açıklaması için bkz http://www.ietf.org.|  
|transferMode|İletileri olup ara belleğe veya akışa veya isteği belirtir veya yanıt. Geçerli değerler şunlardır:<br /><br /> -Arabelleğe: İstek ve yanıt iletilerini arabelleğe.<br />-Akışı: İstek ve yanıt iletileri akışa alınır.<br />-StreamedRequest: İstek iletisi akışı ve yanıt iletisi arabelleğe alındı.<br />-Da StreamedResponse: İstek iletisi arabelleğe alınıp ve yanıt iletisi akışı.<br /><br /> Varsayılan arabelleğe alındı. Bu öznitelik türünde <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Güvenli bağlantı paylaşımı sunucu üzerinde etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısı için bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Makine genelinde proxy ayarlarını yerine kullanıcıya özgü ayarları kullanılıp kullanılmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpTransport` Öğesidir başlangıç noktası HTTP aktarım protokolünü uygulayan bağlaması özel oluşturma için. Birlikte çalışabilirlik amaçlar için kullanılan birincil aktarım HTTP'dir. Bu aktarım diğer WCF Web Hizmetleri yığınları birlikte çalışabilirliği sağlamak için Windows Communication Foundation (WCF) tarafından desteklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
