---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 53f3943524c45a43ddb60553b8ff45f19df66b14
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152469"
---
# \<wsFederation>
<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfad) için yapılandırma sağlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederation>**  
  
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
|authenticationType|Kimlik doğrulama türünü belirten bir URI. WS-Federation oturum açma isteği wauth parametresini ayarlar. İsteğe bağlı. Varsayılan değer, wauth parametresinin isteğe dahil edilmediğini belirten boş bir dizedir.|  
|iği|Dakika cinsinden istenen en fazla kimlik doğrulama isteği süresi. WS-Federation oturum açma isteği wyeni parametresini ayarlar. İsteğe bağlı. Varsayılan değer sıfırdır. İsteğe bağlı. **Uyarı:**  .NET Framework 4,5 ' nin sonraki sürümünde, `freshness` öznitelik türü olur `xs:string` ve varsayılan değer olacaktır `null` .|  
|homeRealm|Kimlik doğrulaması için kullanılacak kimlik sağlayıcısının (IDP) giriş bölgesi. WS-Federation oturum açma isteği whr parametresini ayarlar. İsteğe bağlı. Varsayılan değer, WS parametresinin isteğe dahil edilmediğini belirten boş bir dizedir.|  
|yayınlayan|Amaçlanan belirteç verenin URI 'SI. WS-Federation oturum açma isteklerinin temel URL 'sini ve gereken oturum kapatma isteklerini ayarlar.|  
|persistentCookiesOnPassiveRedirects|Kimlik doğrulamasında kalıcı tanımlama bilgilerinin verilip verilmeyeceğini belirtir. İsteğe bağlı. Varsayılan değer "false", tanımlama bilgileri çıkarılmaz.|  
|passiveRedirectEnabled|WSFAE 'nin yetkisiz istekleri bir STS 'ye otomatik olarak yönlendirmesi için etkinleştirilip etkinleştirilmediğini belirtir. İsteğe bağlı. Varsayılan değer "true", yetkisiz istekler otomatik olarak yönlendirilir.|  
|ilke|Oturum açma isteklerinde kullanılacak ilgili ilkenin konumunu belirten bir URL. Varsayılan değer boş bir dizedir. WS-Federation oturum açma isteği WP parametresini ayarlar. İsteğe bağlı. Varsayılan değer, WP parametresinin isteğe dahil edilmediğini belirten boş bir dizedir.|  
|bölgesindeki|İstenen bölgenin URI 'SI. (Güvenlik belirteci hizmeti (STS) için bağlı olan tarafı (RP) tanımlayan bir URI.) Wtrealm WS-Federation oturum açma isteği parametresini ayarlar. Gereklidir.|  
|döndürüp|Bağlı olan taraf (RP) uygulamasının güvenlik belirteci hizmetinden (STS) yanıt almak istediği adresi tanımlayan bir URL. WS-Federation oturum açma isteği wreply parametresini ayarlar. İsteğe bağlı. Varsayılan değer, wreply parametresinin isteğe dahil edilmediğini belirten boş bir dizedir.|  
|istek|Belirteç verme isteği. WS-Federation oturum açma isteği Wreq parametresini ayarlar. İsteğe bağlı. Varsayılan değer, wreq parametresinin isteğe dahil edilmediğini belirten boş bir dizedir. İstekte wreq veya wreqptr parametresinin dahil edilmesi gerekmez, STS 'nin ne tür bir belirteç olduğunu bilmesini sağlar.|  
|requestPtr|Belirteç verme isteğinin konumunu belirten bir URL. İstek wreqptr parametresini ayarlar. İsteğe bağlı. Varsayılan değer, wreqptr parametresinin isteğe dahil edilmediğini belirten boş bir dizedir. İstekte wreq veya wreqptr parametresinin dahil edilmesi gerekmez, STS 'nin ne tür bir belirteç olduğunu bilmesini sağlar.|  
|requireHttps|Güvenlik belirteci hizmeti (STS) ile iletişimin HTTPS protokolünü kullanması gerekip gerekmediğini belirtir. İsteğe bağlı. Varsayılan değer "true", HTTPS kullanılmalıdır.|  
|kaynak|Erişilen kaynağı, bağlı olan taraf (RP) ile güvenlik belirteci hizmeti 'ne (STS) tanıtan bir URI. İsteğe bağlı. WS-Federation oturum açma isteği wres parametresini ayarlar. İsteğe bağlı. Varsayılan değer, wres parametresinin isteğe dahil edilmediğini belirten boş bir dizedir. **Note:** wres, eski bir parametredir. `realm`Bunun yerine wtrealm parametresini kullanmak için özniteliği belirtin.|  
|SignInQueryString|WS-Federation oturum açma isteği URL 'sinde uygulama tanımlı sorgu parametrelerini belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan değer, isteğe ek parametre ekleneceğini belirten boş bir dizedir. Parametreler, aşağıdaki biçimi kullanarak bir sorgu dizesi parçası olarak belirtilir: ve bu `"param1=value1&param2=value2&param3=value3"` şekilde devam eder. **Note:**  Yapılandırma dosyasında, sorgu dizesindeki ' & "karakteri, varlık başvurusu kullanılarak belirtilmelidir `&` .|  
|signOutQueryString|WS-Federation oturum açma isteği URL 'sinde uygulama tanımlı sorgu parametrelerini belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan değer, isteğe ek parametre ekleneceğini belirten boş bir dizedir. Parametreler, aşağıdaki biçimi kullanarak bir sorgu dizesi parçası olarak belirtilir: ve bu `"param1=value1&param2=value2&param3=value3"` şekilde devam eder. **Note:**  Yapılandırma dosyasında, sorgu dizesindeki ' & "karakteri, varlık başvurusu kullanılarak belirtilmelidir `&` .|  
|signOutReply|WS-Federation protokolü aracılığıyla pasif kayıt sırasında istemcinin güvenlik belirteci hizmeti (STS) tarafından yeniden yönlendirilmesi gereken URL 'YI belirtir. WS-Federation oturum kapatma isteğindeki wreply parametresini ayarlar. İsteğe bağlı. Varsayılan değer, isteğe ek parametre ekleneceğini belirten boş bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfab) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<wsFederation>`Varsayılan WS-Federation parametre ayarlarını ve varsayılan olarak wsfae davranışını yapılandırmak için öğesini kullanabilirsiniz. WS-Federation parametre ayarları, `<wsFederation>` sınıf tarafından kullanıma sunulan eşdeğer özellikler kümesi öğesi altında tanımlanmıştır <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> . Bu özellikler, WSFAE tarafından verilen her istek için aynı kalır. WS-Federation parametrelerini, istek işleme sırasında, WSFAD; tarafından sunulan olaylar için olay işleyicileri ekleyerek dinamik olarak değiştirebilirsiniz. Örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. Daha fazla bilgi için, sınıfının belgelerine bakın <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> .  
  
 `<wsFederation>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.WSFederationElement> . Yapılandırma nesnesinin kendisi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> . <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>Özelliği aracılığıyla erişilen nesne üzerinde tek bir örnek ayarlanır <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ve wsfad için yapılandırma sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML, `<wsFederation>` WSFAD için ayarları belirten bir öğe gösterir.  
  
> [!WARNING]
> Bu örnekte, WSFAE 'nin HTTPS kullanması gerekmez. Bunun nedeni, `requireHttps` `<wsFederation>` öğesindeki özniteliği ayarlanmıştır `false` . Bu ayar, çoğu üretim ortamında bir güvenlik riski sunabilecek şekilde önerilmez.  
  
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
