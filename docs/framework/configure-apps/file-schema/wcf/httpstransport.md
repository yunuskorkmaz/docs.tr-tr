---
title: <httpsTransport>
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: c7e4dc540458bbfb69318d2f14cfa9776f444c55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172828"
---
# <a name="httpstransport"></a>\<httpsTransport>
İçin özel bir bağlama için SOAP iletilerini ileten bir HTTP aktarımı belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<httpsTransport>  
  
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
|allowCookies|İstemcinin tanımlama bilgilerini kabul eder ve bunları gelecekteki isteklerde yayar belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullanan ASMX Web Hizmetleri ile etkileşim kurduğunuzda bu özniteliği kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerini aydaki hizmet için tüm istemci isteklerini otomatik olarak kopyalanır emin olabilirsiniz.|  
|AuthenticationScheme|HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Özet: Özet kimlik doğrulaması belirtir.<br />-Anlaşma: Kimlik doğrulama düzeni belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi takdirde, NTLM kullanılır.<br />-   Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: Temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>. Bu öznitelik yalnızca bir kez ayarlanabilir.|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel Adres yerel ağ veya intranet biridir.<br /><br /> Windows Communication Foundation (WCF) hizmeti adresi ile başlıyorsa proxy her zaman yoksayar `http://localhost`.<br /><br /> Hizmetler için aynı makinede konuşurken bir proxy üzerinden Git istemcilerin istiyorsanız localhost yerine ana bilgisayar adı kullanmanız gerekir.|  
|hostnameComparisonMode|URI ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir. Geçerli değerler,<br /><br /> -StrongWildcard: ("+") bağlamında belirtilen şema, bağlantı noktası ve göreli URI, tüm olası ana bilgisayar adları ile eşleşir.<br />-Tam: joker<br />-WeakWildcard: ("\*") bağlamında belirtilen şema, bağlantı noktası ve açıkça eşlenen olmayan göreli UIR ya da güçlü bir joker karakter mekanizması aracılığıyla olası tüm ana bilgisayar adı ile eşleşir.<br /><br /> StrongWildcard varsayılandır. Bu öznitelik türünde `System.ServiceModel.HostnameComparison`.|  
|manualAddressing|Kullanıcının ileti adresleme denetimini ele geçirmesine olanak tanıyan bir Boole değeri. Bu özellik, genellikle Uygulama ileti göndermek için çeşitli hedeflere aşağıdakilerden hangisi yeri belirler yönlendirici senaryolarda kullanılır.<br /><br /> Ayarlandığında `true`, kanala ileti zaten ele ve ek bilgiler için eklemez varsayar. Kullanıcı ardından her ileti tek tek ele alabilirsiniz.<br /><br /> Ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adresleme mekanizmasını tüm iletiler için adresleri otomatik olarak oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı. 524288 varsayılandır.<br /><br /> WCF pek çok bölümünün arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|maxBufferSize|Arabelleğin en büyük boyutunu belirten pozitif bir tamsayı. 524288 varsayılandır|  
|maxReceivedMessageSize|Alınan izin verilen en büyük ileti boyutunu belirten pozitif bir tamsayı. 65536 varsayılandır.|  
|proxyAddress|HTTP proxy adresini belirten bir URI. Varsa `useSystemWebProxy` olduğu `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|HTTP proxy tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılan protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Kimlik doğrulaması gerçekleştirilir.<br />-Özet: Özet kimlik doğrulaması belirtir.<br />-Anlaşma: Kimlik doğrulama düzeni belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi takdirde, NTLM kullanılır.<br />-   Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: Temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>. Unutmayın <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> desteklenmiyor.|  
|Bölge|Proxy/sunucuda kullanmak için ölge belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Sunucuları, korumalı kaynakların bölümlemek için bölgeleri kullanır. Her bölüm kendi kimlik doğrulama şeması ve/veya yetkilendirme veritabanına sahip olabilir. Bölge kullanımını etkinleştir, yalnızca temel için kullanılır ve Özet kimlik doğrulaması. Bir istemcinin kimliğini başarıyla doğrulayan, sonra kimlik doğrulama, belirli bir bölgedeki tüm kaynaklar için geçerlidir. RFC 2617 en bölgeleri ayrıntılı bir açıklaması için bkz. [IETF Web sitesi](https://www.ietf.org).|  
|requireClientCertificate|Sunucunun HTTPS el sıkışmasının bir parçası olarak bir istemci sertifikası sağlanması için sunucunun istemci gerektirip gerektirmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|transferMode|İletileri ara belleğe veya akışa veya bir istek belirtir veya yanıt. Geçerli değerler şunlardır:<br /><br /> -Arabelleğe alındı: İstek ve yanıt iletileri arabelleğe alınır.<br />-Akış: İstek ve yanıt iletilerinin aktarılır.<br />-StreamedRequest: İstek iletisi sağlanacağına ve yanıt iletisi arabelleğe alındı.<br />-   StreamedResponse: İstek iletisi arabelleğe alınır ve yanıt iletisi akış.<br /><br /> Varsayılan arabelleğe alınır. Bu öznitelik türünde <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Güvensiz bağlantı paylaşımının sunucu üzerinde etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısı için bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Makine genelindeki proxy ayarlarının kullanıcıya özel ayarlar yerine kullanılır olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpsTransport` Öğesi, başlangıç noktası HTTPS Aktarım Protokolü uygulayan özel bağlamayı oluşturmak için. Güvenli birlikte çalışabilirlik amaçlarıyla kullanılan birincil taşıma https'dir. HTTPS, diğer Web hizmetlerini yığınları birlikte çalışabilirliği sağlamak için Windows Communication Foundation (WCF) tarafından desteklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
