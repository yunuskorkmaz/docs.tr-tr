---
title: '&lt;httpsTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b6e89c0caac2ad1d967dedeecbb83e5779f9388
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
SOAP iletilerine özel bağlama için iletmek için bir HTTP taşıması belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<httpsTransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<httpsTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxBufferSize="Integer"  
    maxReceivedMessageSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"        realm="String"  
    requireClientCertificate=Boolean"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
....useDefaultWebProxy="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowCookies|İstemcinin tanımlama bilgilerini kabul eder ve sonraki isteklerde yayar belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Tanımlama bilgileri kullan ASMX Web Hizmetleri ile etkileşim kurarken, bu öznitelik kullanabilirsiniz. Bu şekilde, sunucudan döndürülen tanımlama bilgilerini tüm gelecekteki istemci isteklerine hizmet otomatik olarak kopyalandığından emin olabilir.|  
|authenticationScheme|Bir HTTP dinleyicisi tarafından işlenen istemci isteklerinin kimliğini doğrulamak için kullanılacak protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Özeti: Özet kimlik doğrulaması belirtir.<br />-Anlaş: kimlik doğrulama düzenini belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulamasını belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>. Bu öznitelik yalnızca bir kez ayarlanabilir.|  
|bypassProxyOnLocal|Yerel adresler için proxy sunucuyu atla kılmayacağını gösteren bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Yerel bir adres yerel LAN ya da intranet biridir.<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]her zaman hizmeti adresi http://localhost ile başlıyorsa proxy yok sayar.<br /><br /> İstemcileri bir proxy üzerinden hizmetler için aynı makinede konuşurken gitmek için isterseniz localhost yerine ana bilgisayar adı kullanmanız gerekir.|  
|hostnameComparisonMode|URI'ler ayrıştırmak için kullanılan HTTP ana bilgisayar adı karşılaştırma modunu belirtir. Geçerli değerler,<br /><br /> -StrongWildcard: ("+") belirtilen şema, bağlantı noktası ve göreli URI bağlamında tüm olası ana bilgisayar adı ile eşleşir.<br />-Tam: joker<br />-WeakWildcard: ("*") bağlamında belirtilen düzenini, bağlantı noktası ve açıkça eşlenen olmayan göreli UIR ya da güçlü joker mekanizması aracılığıyla olası tüm ana bilgisayar adı ile eşleşir.<br /><br /> StrongWildcard varsayılandır. Bu öznitelik türünde `System.ServiceModel.HostnameComparison`.|  
|manualAddressing|Kullanıcının ileti adresleme denetimini olanak tanıyan bir Boole değeri. Bu özellik genellikle burada hangisinin bir ileti göndermek için birden fazla hedef uygulama belirler yönlendirici senaryolarda kullanılır.<br /><br /> Ayarlandığında `true`, ileti zaten giderilmiş ve ek bilgiler için eklemez kanal varsayar. Kullanıcı daha sonra her ileti tek tek ele alabilir.<br /><br /> Ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adresleme mekanizması adresleri tüm iletiler için otomatik olarak oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzu boyutunun üst sınırını belirtir pozitif bir tamsayı. 524288 varsayılandır.<br /><br /> WCF pek çok bölümü arabellekleri kullanın. Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez. Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.|  
|maxBufferSize|Arabelleğin en büyük boyutu belirtir pozitif bir tamsayı. 524288 varsayılandır|  
|MaxReceivedMessageSize|Alınabilir maksimum izin verilen ileti boyutunu belirtir pozitif bir tamsayı. 65536 varsayılandır.|  
|proxyAddress|HTTP proxy adresini belirtir URI. Varsa `useSystemWebProxy` olan `true`, bu ayar olmalıdır `null`. Varsayılan, `null` değeridir.|  
|proxyAuthenticationScheme|Bir HTTP proxy'si tarafından işlenen istemci isteklerinin kimlik doğrulaması için kullanılacak protokolü belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Kimlik doğrulaması gerçekleştirilmez.<br />-Özeti: Özet kimlik doğrulaması belirtir.<br />-Anlaş: kimlik doğrulama düzenini belirlemek için istemci ile görüşür. İstemci ve sunucu Kerberos destekliyorsa, kullanılır; Aksi halde, NTLM kullanılır.<br />-Ntlm: NTLM kimlik doğrulaması belirtir.<br />-Temel: temel kimlik doğrulaması belirtir.<br />-Anonim: Anonim kimlik doğrulamasını belirtir.<br />-IntegratedWindowsAuthentication: Windows kimlik doğrulaması belirtir.<br /><br /> Anonim varsayılandır. Bu öznitelik türünde <xref:System.Net.AuthenticationSchemes>.|  
|Bölge|Proxy/sunucuda kullanmak için bölge belirten bir dize. Varsayılan boş bir dizedir.<br /><br /> Sunucuları, korunan kaynaklara bölümlemek için bölgeleri kullanır. Her bölüm kendi kimlik doğrulama düzeni ve/veya yetkilendirme veritabanına sahip olabilir. Bölge için basic kullanılır ve Özet kimlik doğrulaması. Bir istemci kimliğini başarıyla doğrulayan sonra kimlik doğrulama, belirli bir bölgedeki tüm kaynaklar için geçerlidir. Bölge ayrıntılı bir açıklaması için RFC 2617 http://www.ietf.org bakın.|  
|RequireClientCertificate|Sunucunun HTTPS el sıkışmasının bir parçası olarak bir istemci sertifikası sağlamak için istemcinin gerektirip gerektirmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|transferMode|İletileri olup ara belleğe veya akışa veya isteği belirtir veya yanıt. Geçerli değerler şunlardır:<br /><br /> -Arabelleğe: İstek ve yanıt iletilerini arabelleğe.<br />-Akışı: İstek ve yanıt iletileri akışa alınır.<br />-StreamedRequest: İstek iletisi akışı ve yanıt iletisi arabelleğe alındı.<br />-Da StreamedResponse: İstek iletisi arabelleğe alınıp ve yanıt iletisi akışı.<br /><br /> Varsayılan arabelleğe alındı. Bu öznitelik türünde <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Güvenli bağlantı paylaşımı sunucu üzerinde etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir. Etkinleştirilirse, NTLM kimlik doğrulaması her TCP bağlantısı için bir kez gerçekleştirilir.|  
|useDefaultWebProxy|Makine genelinde proxy ayarlarını yerine kullanıcıya özgü ayarları kullanılıp kullanılmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `httpsTransport` Öğesidir başlangıç noktası için bir özel, bağlama oluşturma HTTPS aktarım protokolünü uygular. HTTPS güvenli birlikte çalışabilirlik amaçlar için kullanılan birincil Aktarım ' dir. HTTPS tarafından desteklenen [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] diğer Web ile birlikte çalışabilirlik yığınları hizmetleri sağlamak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.HttpsTransportElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
