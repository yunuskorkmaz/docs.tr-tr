---
title: '&lt;cookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fcdf1e89c3b68daa36ee80fe7234737c61a5a3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcookiehandlergt"></a>&lt;cookieHandler&gt;
Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) okuma ve yazma tanımlama için kullanır.  
  
 \<system.identityModel.services >  
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
|name|Yazılan tüm tanımlama bilgilerini temel adını belirtir. Varsayılan değer "FedAuth" dir.|  
|yol|Yazılan hiçbir tanımlama bilgisi yolu değerini belirtir. Varsayılan değer "HttpRuntime.AppDomainAppVirtualPath" dir.|  
|mod|Aşağıdakilerden birini <xref:System.IdentityModel.Services.CookieHandlerMode> SAM tarafından kullanılan tanımlama bilgisi işleyicisi türünü belirten değer. Aşağıdaki değerler kullanılabilir:<br /><br /> -"Varsayılan" — "Chunked" ile aynı.<br />-"Öbekli" — bir örneğini kullanan <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı. Bu tanımlama bilgisi işleyicisi tanımlama bilgilerini bağımsız kümesi en fazla boyutu aşmamasını sağlar. Bu büyük olasılıkla "mantıksal bir tanımlama bilgisi tanımlama bilgileri üzerinde hat sayıya Öbekleme tarafından" tamamlanır.<br />-"Özel" — türetilen özel bir sınıf örneği kullanan <xref:System.IdentityModel.Services.CookieHandler>. Türetilmiş sınıf tarafından başvuruluyor `<customCookieHandler>` alt öğesi.<br /><br /> "Varsayılan" varsayılandır.|  
|persistentSessionLifetime|Kalıcı oturum yaşam süresini belirtir. Geçici oturum sıfır ise, her zaman kullanılır. Geçici oturum belirtir "0:0:0" varsayılan değerdir. Bir oturum 365 gün belirtir "365:0:0" en yüksek değerdir. Aşağıdaki kısıtlama göre değer belirtilmeli: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, burada en soldaki değerini günleri belirtir, orta değer (varsa) saatleri belirtir ve dakika (varsa) en sağdaki değerini belirtir.|  
|requireSsl|"Güvenli" bayrağı yazılan tüm tanımlama bilgilerini yayılan olup olmadığını belirtir. Bu değer ayarlanırsa, oturum açma oturum tanımlama bilgileri yalnızca HTTPS üzerinden kullanılabilir. Varsayılan değer "true" ise.|  
|hideFromScript|"HttpOnly" bayrağı yazılan tüm tanımlama bilgilerini yayılan olup olmadığını denetler. Bazı web tarayıcıları, istemci tarafı komut dosyası tanımlama bilgisi değeri erişmesini tutarak bu bayrak kabul. Varsayılan değer "true" ise.|  
|etki alanı|Yazılan tanımlama bilgisinin etki alanı değeri. Varsayılan değer "".|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<chunkedCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Bu öğe yalnızca mevcut olabilir, `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".|  
|[\<customCookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|Özel tanımlama bilgisi işleyici türünü ayarlar. Bu öğe mevcut olması durumunda `mode` özniteliği `<cookieHandler>` öğesidir "Özel". Tüm diğer değerleri için mevcut olamaz `mode` özniteliği. Özel tür öğesinden türetilmelidir <xref:System.IdentityModel.Services.CookieHandler> sınıfı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.IdentityModel.Services.CookieHandler> Düzeyi okuma ve yazma ham tanımlama bilgileri, HTTP protokolü için sorumludur. Ya da yapılandırabileceğiniz bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> veya özel tanımlama bilgisi işleyici türetilmiş <xref:System.IdentityModel.Services.CookieHandler> sınıfı.  
  
 Parçalı tanımlama bilgileri işleyici yapılandırmak için "Chunked" veya "Varsayılan" mod özniteliği ayarlayın. Varsayılan öbek boyutu 2000 bayt, ancak ekleyerek isteğe bağlı olarak farklı öbek boyutu belirtebilir bir `<chunkedCookieHandler>` alt öğesi.  
  
 Bir özel tanımlama bilgisi işleyici yapılandırmak için "Özel" moduna özniteliğine ayarlayın. Ayrıca belirtmelisiniz bir `<customCookieHandler>` özel işleyicinizi türüne başvuran alt öğesi.  
  
 `<cookieHandler>` Öğesi ile temsil edilir <xref:System.IdentityModel.Services.CookieHandlerElement> sınıfı. Yapılandırmada belirtilen tanımlama bilgisi işleyici kullanılabilir <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> özelliği <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> üzerinde ayarlanmış nesnesi <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<cookieHandler>` öğesi. Bu örnekte, çünkü `mode` özniteliği belirtilmezse, varsayılan tanımlama bilgisi işleyici SAM tarafından kullanılır. Bu örneği olan <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfı. Çünkü `<chunkedCookieHandler>` alt öğesi belirtilmemişse, varsayılan öbek boyutu kullanılır. Çünkü HTTPS gerekli olmayacak `requireSsl` özniteliğinin ayarlanmış `false`.  
  
> [!WARNING]
>  Bu örnekte, HTTPS, oturum tanımlama bilgileri yazmak için gerekli değildir. Bunun nedeni, `requireSsl` özniteliği `<cookieHandler>` ayarlanır `false`. Bu ayar bir güvenlik riski sayılabilir çoğu üretim ortamları için önerilmez.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
