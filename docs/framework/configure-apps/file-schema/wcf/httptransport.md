---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: d03b92dc1e7b53a182b8065a6d4ac652f76291ba
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147440"
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
İçin özel bir bağlama için SOAP iletilerini ileten bir HTTP aktarımı belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
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
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous/IntegratedWindowsAuthentication"
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
|allowCookies|İstemcinin tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullanan ASMX Web Hizmetleri ile etkileşim kurduğunuzda bu özniteliği kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerini aydaki hizmet için tüm istemci isteklerini otomatik olarak kopyalanır emin olabilirsiniz.|  
|AuthenticationScheme|HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Özet: Özet kimlik doğrulaması belirtir.<br />-Anlaşma: Kimlik doğrulama düzeni belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi takdirde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: Temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>. Bu öznitelik yalnızca bir kez ayarlanabilir.|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel Adres yerel ağ veya intranet biridir.<br /><br /> Windows Communication Foundation (WCF) hizmeti adresi ile başlıyorsa proxy her zaman yoksayar `http://localhost`.<br /><br /> Hizmetler için aynı makinede konuşurken bir proxy üzerinden Git istemcilerin istiyorsanız localhost yerine ana bilgisayar adı kullanmanız gerekir.|  
|hostnameComparisonMode|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Geçerli değerler,<br /><br /> -StrongWildcard: ("+") bağlamında belirtilen şema, bağlantı noktası ve göreli URI, tüm olası ana bilgisayar adları ile eşleşir.<br />-Tam: joker<br />-WeakWildcard: ("\*") bağlamında belirtilen şema, bağlantı noktası ve açıkça eşlenen olmayan göreli UIR ya da güçlü bir joker karakter mekanizması aracılığıyla olası tüm ana bilgisayar adı ile eşleşir.<br /><br /> StrongWildcard varsayılandır. Bu öznitelik türünde `System.ServiceModel.HostnameComparisonMode`.|  
|keepAliveEnabled|Internet kaynağıyla kalıcı bir bağlantı kurmak belirten bir Boole değeri.|  
|maxBufferSize|Arabelleğin en büyük boyutunu belirten pozitif bir tamsayı. 524288 varsayılandır|  
|proxyAddress|HTTP proxy adresini belirten bir URI. Varsa `useSystemWebProxy` olduğu `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Kimlik doğrulaması gerçekleştirilir.<br />-Özet: Özet kimlik doğrulaması belirtir.<br />-Anlaşma: Kimlik doğrulama düzeni belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi takdirde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: Temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulaması belirtir.<br />-Backendserverauthenticationmode: Windows kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>.|  
|Bölge|Proxy/sunucuda kullanmak için ölge belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Sunucuları, korumalı kaynakların bölümlemek için bölgeleri kullanır. Her bölüm kendi kimlik doğrulama şeması ve/veya yetkilendirme veritabanına sahip olabilir. Bölge kullanımını etkinleştir, yalnızca temel için kullanılır ve Özet kimlik doğrulaması. Bir istemcinin kimliğini başarıyla doğrulayan, sonra kimlik doğrulama, belirli bir bölgedeki tüm kaynaklar için geçerlidir. RFC 2617 en bölgeleri ayrıntılı bir açıklaması için bkz. [IETF Web sitesi](https://www.ietf.org).|  
|transferMode|İletileri ara belleğe veya akışa veya bir istek belirtir veya yanıt. Geçerli değerler şunlardır:<br /><br /> -Arabelleğe alındı: İstek ve yanıt iletileri arabelleğe alınır.<br />-Akış: İstek ve yanıt iletilerinin aktarılır.<br />-StreamedRequest: İstek iletisi sağlanacağına ve yanıt iletisi arabelleğe alındı.<br />-Da StreamedResponse: İstek iletisi arabelleğe alınır ve yanıt iletisi akış.<br /><br /> Varsayılan arabelleğe alınır. Bu öznitelik türünde <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Güvensiz bağlantı paylaşımının sunucu üzerinde etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısı için bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Makine genelindeki proxy ayarlarının kullanıcıya özel ayarlar yerine kullanılır olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpTransport` Öğesi, başlangıç noktası HTTP aktarım protokolünü uygulayan özel bağlamayı oluşturmak için. Birlikte çalışabilirlik amaçlarıyla kullanılan birincil taşıma HTTP'dir. Bu aktarım diğer WCF Web Hizmetleri yığınları birlikte çalışabilirliği sağlamak için Windows Communication Foundation (WCF) tarafından desteklenir.  
  
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
