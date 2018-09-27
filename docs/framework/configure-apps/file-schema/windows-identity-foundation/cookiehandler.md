---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 99bf6edb4e4f631eba292990c65c1f0c8553d8c0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235302"
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> okuma ve yazma tanımlama bilgileri (SAM) kullanır.  
  
 \<System.IdentityModel.Services >  
\<Federationconfiguration'a >  
\<cookieHandler >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Yazılan tüm tanımlama bilgilerini temel adını belirtir. "FedAuth" varsayılandır.|  
|yol|Yazılan tüm tanımlama bilgilerini yol değeri belirtir. "HttpRuntime.AppDomainAppVirtualPath" varsayılandır.|  
|mod|Aşağıdakilerden birini <xref:System.IdentityModel.Services.CookieHandlerMode> SAM tarafından kullanılan tanımlama bilgisi işleyicisi türünü belirten değer. Aşağıdaki değerler kullanılabilir:<br /><br /> -"Varsayılan"-"Öbekli" ile aynı.<br />-"Öbekli" — bir örneği kullanan <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı. Bu tanımlama bilgisi işleyicisi tanımlama bilgilerini bağımsız kümesi en fazla boyutu aşmamasını sağlar. Bu büyük olasılıkla "mantıksal bir tanımlama bilgisi tanımlama bilgisi-hat üzerinde bir dizi Öbekleme tarafından" gerçekleştirir.<br />-"Özel" — öğesinden türetilen özel bir sınıf örneği kullanan <xref:System.IdentityModel.Services.CookieHandler>. Türetilmiş sınıf tarafından başvurulan `<customCookieHandler>` alt öğesi.<br /><br /> "Varsayılan" varsayılandır.|  
|persistentSessionLifetime|Kalıcı oturum ömrünü belirtir. Sıfır ise, geçici oturumları her zaman kullanılır. Geçici bir oturum belirtir "0:0:0" varsayılan değerdir. En fazla 365 günlük bir oturumu belirtir "365:0:0" değeridir. Değere göre aşağıdaki kısıtlama belirtilmelidir: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, burada en soldaki değerin gün, saat Orta (varsa) değerini belirtir ve sağdaki değerin (varsa) dakika belirtir.|  
|İçindeki requireSSL öğesini|Yazılan tüm tanımlama bilgilerini "Güvenli" bayrak yayılan olup olmadığını belirtir. Bu değeri ayarlarsanız, oturum açma oturum tanımlama bilgileri yalnızca HTTPS üzerinden kullanılabilir. Varsayılan değer "true" ise.|  
|hideFromScript|Yazılan tüm tanımlama bilgilerini "HttpOnly" bayrak yayılan olup olmadığını denetler. Bazı web tarayıcıları, istemci tarafı komut dosyası tanımlama bilgisi değeri erişmesini tutarak bu bayrağı oluşuyor. Varsayılan değer "true" ise.|  
|etki alanı|Yazılan tüm tanımlama bilgilerini etki alanı değeri. Varsayılan değer "".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Bu öğe yalnızca mevcut olması durumunda `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Özel bir tanımlama bilgisi işleyici türünü ayarlar. Bu öğe bulunmalıdır, `mode` özniteliği `<cookieHandler>` "Özel" bir öğedir. Herhangi diğer değerleri için bulunamaz `mode` özniteliği. Özel tür nesnesinden türetilmesi <xref:System.IdentityModel.Services.CookieHandler> sınıfı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarları içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.IdentityModel.Services.CookieHandler> Düzeyi okuma ve yazma ham tanımlama bilgisi, HTTP protokolü için sorumludur. Ya da yapılandırabileceğiniz bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> veya özel bir tanımlama bilgisi işleyicisi türetilmiş <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 Öbekli tanımlama bilgisi işleyici yapılandırmak için "Öbekli" veya "Varsayılan" modunda özniteliği ayarlayın. Varsayılan öbek boyutu 2000 bayt, ancak dahil ederek isteğe bağlı olarak farklı öbek boyutu belirtebilirsiniz bir `<chunkedCookieHandler>` alt öğesi.  
  
 Özel bir tanımlama bilgisi işleyiciyi yapılandırmanız için modu özniteliğini "Özel" olarak ayarlayın. De belirtmeniz gerekir bir `<customCookieHandler>` özel işleyicinizi türe başvuran alt öğesi.  
  
 `<cookieHandler>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Services.CookieHandlerElement> sınıfı. Yapılandırmada belirtilen tanımlama bilgisi işleyici kullanılabilir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> özelliği <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> nesnesi üzerinde ayarlayın <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<cookieHandler>` öğesi. Bu örnekte, çünkü `mode` özniteliği belirtilmezse, varsayılan tanımlama bilgisi işleyici tarafından SAM kullanılır. Bunun bir örneğidir <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı. Çünkü `<chunkedCookieHandler>` alt öğe belirtilmemişse, varsayılan öbek boyutu kullanılır. Çünkü HTTPS gerekli olmayacak `requireSsl` özniteliği `false`.  
  
> [!WARNING]
>  Bu örnekte, HTTPS oturum tanımlama bilgileri yazmak için gerekli değildir. Bunun nedeni, `requireSsl` özniteliği `<cookieHandler>` ayarlanır `false`. Bu ayar, bir güvenlik riski sunabilir gibi çoğu üretim ortamları için önerilmez.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
