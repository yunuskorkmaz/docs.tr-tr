---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 853dc9817d080e59ac7a792576eda862bd0b1f1d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252033"
---
# \<cookieHandler>
<xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
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
|mod|<xref:System.IdentityModel.Services.CookieHandlerMode>Sam tarafından kullanılan tanımlama bilgisi işleyicisi türünü belirten değerlerden biri. Aşağıdaki değerler kullanılabilir:<br /><br /> -"Varsayılan" — "öbekli" ile aynıdır.<br />-"Öbekli" — sınıfının bir örneğini kullanır <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Bu tanımlama bilgisi işleyicisi, tek tek tanımlama bilgilerinin bir küme en büyük boyutunu aşmamasını sağlar. Bunu, büyük olasılıkla "parçalama" bir mantıksal tanımlama bilgisini çok sayıda tanımlama bilgisine ekleyerek gerçekleştirir.<br />-"Custom" — öğesinden türetilmiş özel bir sınıfın örneğini kullanır <xref:System.IdentityModel.Services.CookieHandler> . Türetilmiş sınıfa `<customCookieHandler>` alt öğe tarafından başvuruluyor.<br /><br /> Varsayılan değer "varsayılan" dır.|  
|persistentSessionLifetime|Kalıcı oturumların yaşam süresini belirtir. Sıfır ise, geçici oturumlar her zaman kullanılır. Varsayılan değer, geçici bir oturum belirten "0:0:0" değeridir. En büyük değer, 365 günlük bir oturum belirten "365:0:0" değeridir. Değer aşağıdaki kısıtlamaya göre belirtilmelidir: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` , en sol değer günler ' i belirttiğinde, ortadaki değer (varsa) saatleri belirtir ve en sağdaki değer (varsa) dakikaları belirtir.|  
|requireSsl|Yazılan tanımlama bilgileri için "güvenli" bayrağının oluşturulup oluşturulmayacağını belirtir. Bu değer ayarlandıysa, oturum açma oturum tanımlama bilgileri yalnızca HTTPS üzerinden kullanılabilir. Varsayılan değer "true" dır.|  
|hideFromScript|Yazılan tanımlama bilgileri için "HttpOnly" bayrağının kullanılıp kullanılmadığını denetler. Belirli Web tarayıcıları, istemci tarafı komut dosyasının tanımlama bilgisi değerine erişmesini sağlayarak bu bayrağı dikkate getirir. Varsayılan değer "true" dır.|  
|etki alanı|Yazılan tanımlama bilgilerinin etki alanı değeri. Varsayılan değer "" dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.|  
|[\<customCookieHandler>](customcookiehandler.md)|Özel tanımlama bilgisi işleyici türünü ayarlar. `mode` `<cookieHandler>` Öğenin özniteliği "Custom" ise bu öğe bulunmalıdır. Özniteliğin diğer değerleri için mevcut olamaz `mode` . Özel tür <xref:System.IdentityModel.Services.CookieHandler> sınıfından türetilmelidir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 , <xref:System.IdentityModel.Services.CookieHandler> Http protokol düzeyinde ham tanımlama bilgilerini okumaktan ve yazmaktan sorumludur. <xref:System.IdentityModel.Services.ChunkedCookieHandler>Sınıfından türetilmiş bir ya da özel tanımlama bilgisi işleyicisi yapılandırabilirsiniz <xref:System.IdentityModel.Services.CookieHandler> .  
  
 Öbekli bir tanımlama bilgisi işleyicisini yapılandırmak için, mode özniteliğini "öbekli" veya "default" olarak ayarlayın. Varsayılan öbek boyutu 2000 bayttır, ancak isteğe bağlı olarak bir alt öğe ekleyerek farklı bir öbek boyutu belirtebilirsiniz `<chunkedCookieHandler>` .  
  
 Özel bir tanımlama bilgisi işleyicisini yapılandırmak için, mode özniteliğini "Custom" olarak ayarlayın. Ayrıca `<customCookieHandler>` , özel işleyicinizin türüne başvuran bir alt öğe belirtmeniz gerekir.  
  
 `<cookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.CookieHandlerElement> . Yapılandırmada belirtilen tanımlama bilgisi işleyicisi, <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> özelliği üzerinde ayarlanan nesnenin özelliğinden kullanılabilir <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML bir öğesini gösterir `<cookieHandler>` . Bu örnekte, `mode` özniteliği belirtilmediği için, varsayılan tanımlama bilgisi IŞLEYICISI Sam tarafından kullanılacaktır. Bu, sınıfının bir örneğidir <xref:System.IdentityModel.Services.ChunkedCookieHandler> . `<chunkedCookieHandler>`Alt öğe belirtilmediği için, varsayılan öbek boyutu kullanılacaktır. Özniteliği ayarlandığından, HTTPS gerekli olmayacaktır `requireSsl` `false` .  
  
> [!WARNING]
> Bu örnekte, oturum tanımlama bilgilerini yazmak için HTTPS gerekli değildir. Bunun nedeni, `requireSsl` `<cookieHandler>` öğesindeki özniteliği olarak ayarlanmıştır `false` . Bu ayar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
