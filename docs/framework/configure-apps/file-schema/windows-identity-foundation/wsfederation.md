---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152469"
---
# <a name="wsfederation"></a>\<wsFederasyon>
<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) için yapılandırma sağlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federasyonKonfigürasyon>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederasyon>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|authenticationType|Kimlik doğrulama türünü belirten bir URI. WS-Federation oturum açma isteği wauth parametresini ayarlar. İsteğe bağlı. Varsayılan, wauth parametresinin isteğe dahil olmadığını belirten boş bir dizedir.|  
|Taze|İstenilen maksimum kimlik doğrulama isteği yaşı, dakika içinde. WS-Federation oturum açma isteği wfresh parametresini ayarlar. İsteğe bağlı. Varsayılan değer sıfırdır. İsteğe bağlı. **Uyarı:**  .NET Framework 4.5'in bir `freshness` sonraki sürümünde öznitelik türde `xs:string` olacak `null`ve varsayılan değeri .|  
|anasayfaDiyar|Kimlik doğrulama için kullanılacak kimlik sağlayıcısının (IdP) ana alanı. WS-Federation oturum açma isteği parametresini ayarlar. İsteğe bağlı. Varsayılan, whr parametrenin isteğe dahil olmadığını belirten boş bir dizedir.|  
|yayınlayan|Amaçlanan belirteç verenin URI' si. WS-Federation oturum açma isteklerinin ve oturum açma isteklerinin temel URL'sini ayarlar.|  
|persistentCookiesOnPassiveRedirects|Kalıcı tanımlama bilgilerinin kimlik doğrulamaüzerinde verilip verilmeyeceğini belirtir. İsteğe bağlı. Varsayılan "false", tanımlama bilgileri verilmez.|  
|pasifRedirectEtkin|WSFAM'nin yetkisiz istekleri otomatik olarak bir STS'ye yönlendirmesinin etkin olup olmadığını belirtir. İsteğe bağlı. Varsayılan "true", yetkisiz istekler otomatik olarak yönlendirilir.|  
|ilke|Oturum açma isteklerinde kullanılacak ilgili ilkenin konumunu belirten bir URL. Varsayılan, boş bir dizedir. WS-Federation oturum açma isteği wp parametresini ayarlar. İsteğe bağlı. Varsayılan, wp parametresinin isteğe dahil olmadığını belirten boş bir dizedir.|  
|Bölge|İstenen diyarın URI'si. (Güvenen tarafı (RP) güvenlik belirteç hizmetine (STS) tanımlayan bir URI.) İstek wtrealm WS-Federation oturum açma isteği parametresini ayarlar. Gereklidir.|  
|Yanıt|Güvenen taraf (RP) uygulamasının Güvenlik Belirteci Hizmeti'nden (STS) yanıt almak istediği adresi tanımlayan bir URL. WS-Federation oturum açma isteği wreply parametresini ayarlar. İsteğe bağlı. Varsayılan, wreply parametresinin isteğe dahil olmadığını belirten boş bir dizedir.|  
|istek|Belirteç verme isteği. WS-Federation oturum açma isteği wreq parametresini ayarlar. İsteğe bağlı. Varsayılan, wreq parametresinin isteğe dahil olmadığını belirten boş bir dizedir. Istek te wreqveya wreqptr parametre dahil değil STS sorunu ne tür belirteç bilir anlamına gelir.|  
|requestPtr|Belirteç verme isteğinin konumunu belirten bir URL. İstek wreqptr parametresini ayarlar. İsteğe bağlı. Varsayılan, wreqptr parametresinin isteğe dahil olmadığını belirten boş bir dizedir. Istek te wreqveya wreqptr parametre dahil değil STS sorunu ne tür belirteç bilir anlamına gelir.|  
|gerektirirHttps|Güvenlik belirteci hizmetiyle (STS) iletişimin HTTPS protokolünü kullanıp kullanmaması gerektiğini belirtir. İsteğe bağlı. Varsayılan "true", HTTPS kullanılmalıdır.|  
|kaynak|Erişilen kaynağı tanımlayan bir URI, güvenen taraf (RP), güvenlik belirteci hizmetine (STS). İsteğe bağlı. WS-Federation oturum açma isteğini wres parametresini ayarlar. İsteğe bağlı. Varsayılan, wres parametresinin isteğe dahil olmadığını belirten boş bir dizedir. **Not:** wres eski bir parametredir. Bunun `realm` yerine wtrealm parametresini kullanmak için özniteliği belirtin.|  
|signInQueryString|WS-Federation oturum açma isteği URL'sinde uygulama tanımlı sorgu parametrelerini belirtmek için genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan, isteğe ek parametre eklenmemesi gerektiğini belirten boş bir dizedir. Parametreler aşağıdaki formu kullanarak bir sorgu dize `"param1=value1&param2=value2&param3=value3"` parçası olarak belirtilir: ve benzeri. **Not:**  Yapılandırma dosyasında sorgu dizesindeki '&' karakteri varlık `&`başvurusu kullanılarak belirtilmelidir.|  
|signOutQueryString|WS-Federation oturum açma isteği URL'sinde uygulama tanımlı sorgu parametrelerini belirtmek için genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan, isteğe ek parametre eklenmemesi gerektiğini belirten boş bir dizedir. Parametreler aşağıdaki formu kullanarak bir sorgu dize `"param1=value1&param2=value2&param3=value3"` parçası olarak belirtilir: ve benzeri. **Not:**  Yapılandırma dosyasında sorgu dizesindeki '&' karakteri varlık `&`başvurusu kullanılarak belirtilmelidir.|  
|signOutReply|WS-Federation protokolü aracılığıyla pasif oturum açma sırasında istemcinin güvenlik belirteci hizmeti (STS) tarafından yönlendirilmesi gereken URL'yi belirtir. Wreply parametresini WS-Federation oturum açma isteğiüzerine ayarlar. İsteğe bağlı. Varsayılan, isteğe ek parametre eklenmemesi gerektiğini belirten boş bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federasyonKonfigürasyon>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) yapılandırılan ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<wsFederation>` Varsayılan WS-Federation parametre ayarlarını ve WSFAM için varsayılan davranışı yapılandırmak için öğeyi kullanabilirsiniz. `<wsFederation>` Sınıf tarafından <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> maruz kalan eşdeğer özellikleri ayarla öğesi altında tanımlanan WS-Federasyon parametre ayarları. Bu özellikler WSFAM tarafından verilen her istek için aynı kalır. WSFAM tarafından maruz kalan olaylar için olay işleyicileri ekleyerek istek işleme sırasında WS-Federation parametrelerini dinamik olarak değiştirebilirsiniz; örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. Daha fazla bilgi için sınıf <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> için belgelere bakın.  
  
 Öğe `<wsFederation>` <xref:System.IdentityModel.Services.Configuration.WSFederationElement> sınıf tarafından temsil edilir. Yapılandırma nesnesinin kendisi <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> sınıf tarafından temsil edilir. Tek <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> bir örnek <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özellik üzerinden erişilen ve WSFAM için yapılandırma sağlayan nesne üzerinde ayarlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, `<wsFederation>` WSFAM ayarlarını belirten bir öğe gösterir.  
  
> [!WARNING]
> Bu örnekte, WSFAM'nin HTTPS kullanması gerekmez. Bunun nedeni, `requireHttps` öğedeki `<wsFederation>` öznitelik `false`kümesidir. Bu ayar, bir güvenlik riski sunabileceğiiçin çoğu üretim ortamı için önerilmez.  
  
```xml
<wsFederation passiveRedirectEnabled="true"
              issuer="http://localhost:15839/wsFederationSTS/Issue"
              realm="http://localhost:50969/"
              reply="http://localhost:50969/"
              requireHttps="false"
              signOutReply="http://localhost:50969/SignedOutPage.html"
              signOutQueryString="Param1=value2&Param2=value2"
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
