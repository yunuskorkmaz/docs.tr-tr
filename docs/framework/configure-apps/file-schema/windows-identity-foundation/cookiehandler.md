---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 853dc9817d080e59ac7a792576eda862bd0b1f1d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252033"
---
# <a name="cookiehandler"></a>\<Tanımlama, ıehandler >
<xref:System.IdentityModel.Services.CookieHandler> (Sam)tanımlamabilgileriniokumakveyazmak<xref:System.IdentityModel.Services.SessionAuthenticationModule> için kullandığı öğesini yapılandırır.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Tanımlama, ıehandler >**  
  
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
|name|Yazılan tanımlama bilgilerinin temel adını belirtir. Varsayılan değer "Fedaduth" ' dir.|  
|yol|Yazılan tanımlama bilgilerinin yol değerini belirtir. Varsayılan değer "HttpRuntime. AppDomainAppVirtualPath" dir.|  
|mod|Sam tarafından kullanılan tanımlama bilgisi işleyicisi türünü belirten değerlerdenbiri.<xref:System.IdentityModel.Services.CookieHandlerMode> Aşağıdaki değerler kullanılabilir:<br /><br /> -"Varsayılan" — "öbekli" ile aynıdır.<br />-"Öbekli" — <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfının bir örneğini kullanır. Bu tanımlama bilgisi işleyicisi, tek tek tanımlama bilgilerinin bir küme en büyük boyutunu aşmamasını sağlar. Bunu, büyük olasılıkla "parçalama" bir mantıksal tanımlama bilgisini çok sayıda tanımlama bilgisine ekleyerek gerçekleştirir.<br />-"Custom" — öğesinden <xref:System.IdentityModel.Services.CookieHandler>türetilmiş özel bir sınıfın örneğini kullanır. Türetilmiş sınıfa `<customCookieHandler>` alt öğe tarafından başvuruluyor.<br /><br /> Varsayılan değer "varsayılan" dır.|  
|persistentSessionLifetime|Kalıcı oturumların yaşam süresini belirtir. Sıfır ise, geçici oturumlar her zaman kullanılır. Varsayılan değer, geçici bir oturum belirten "0:0:0" değeridir. En büyük değer, 365 günlük bir oturum belirten "365:0:0" değeridir. Değer aşağıdaki kısıtlamaya göre belirtilmelidir: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, en sol değer günler ' i belirttiğinde, ortadaki değer (varsa) saatleri belirtir ve en sağdaki değer (varsa) dakikaları belirtir.|  
|requireSsl|Yazılan tanımlama bilgileri için "güvenli" bayrağının oluşturulup oluşturulmayacağını belirtir. Bu değer ayarlandıysa, oturum açma oturum tanımlama bilgileri yalnızca HTTPS üzerinden kullanılabilir. Varsayılan değer "true" dır.|  
|hideFromScript|Yazılan tanımlama bilgileri için "HttpOnly" bayrağının kullanılıp kullanılmadığını denetler. Belirli Web tarayıcıları, istemci tarafı komut dosyasının tanımlama bilgisi değerine erişmesini sağlayarak bu bayrağı dikkate getirir. Varsayılan değer "true" dır.|  
|etki alanı|Yazılan tanımlama bilgilerinin etki alanı değeri. Varsayılan değer "" dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Öbek için yığın tanımlama >](chunkedcookiehandler.md)|Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.|  
|[\<Custombir ıehandler >](customcookiehandler.md)|Özel tanımlama bilgisi işleyici türünü ayarlar. `mode` Öğenin özniteliği`<cookieHandler>` "Custom" ise bu öğe bulunmalıdır. `mode` Özniteliğin diğer değerleri için mevcut olamaz. Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federationConfiguration >](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (Wsfab) <xref:System.IdentityModel.Services.SessionAuthenticationModule> ve (Sam) yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 , <xref:System.IdentityModel.Services.CookieHandler> Http protokol düzeyinde ham tanımlama bilgilerini okumaktan ve yazmaktan sorumludur. Sınıfından<xref:System.IdentityModel.Services.CookieHandler> türetilmiş bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> ya da özel tanımlama bilgisi işleyicisi yapılandırabilirsiniz.  
  
 Öbekli bir tanımlama bilgisi işleyicisini yapılandırmak için, mode özniteliğini "öbekli" veya "default" olarak ayarlayın. Varsayılan öbek boyutu 2000 bayttır, ancak isteğe bağlı olarak bir `<chunkedCookieHandler>` alt öğe ekleyerek farklı bir öbek boyutu belirtebilirsiniz.  
  
 Özel bir tanımlama bilgisi işleyicisini yapılandırmak için, mode özniteliğini "Custom" olarak ayarlayın. Ayrıca, özel işleyicinizin `<customCookieHandler>` türüne başvuran bir alt öğe belirtmeniz gerekir.  
  
 `<cookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Services.CookieHandlerElement> tarafından temsil edilir. Yapılandırmada belirtilen tanımlama bilgisi işleyicisi, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği üzerinde ayarlanan <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> nesnenin özelliğinden kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML bir `<cookieHandler>` öğesini gösterir. Bu örnekte, `mode` özniteliği belirtilmediği için, varsayılan tanımlama bilgisi işleyicisi Sam tarafından kullanılacaktır. Bu, <xref:System.IdentityModel.Services.ChunkedCookieHandler> sınıfının bir örneğidir. `<chunkedCookieHandler>` Alt öğe belirtilmediği için, varsayılan öbek boyutu kullanılacaktır. `requireSsl` Özniteliği ayarlandığından`false`, https gerekli olmayacaktır.  
  
> [!WARNING]
> Bu örnekte, oturum tanımlama bilgilerini yazmak için HTTPS gerekli değildir. Bunun nedeni `requireSsl` , `<cookieHandler>` öğesindeki özniteliği olarak `false`ayarlanmıştır. Bu ayar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
