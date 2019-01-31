---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: 801970ec05fc88587a5b45b5bb3a855d1a81afb3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285888"
---
# <a name="wsfederation"></a>\<wsFederation >
İçin yapılandırma sağlar <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<System.IdentityModel.Services >  
\<Federationconfiguration'a >  
\<wsFederation >  
  
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
|authenticationType|Kimlik doğrulaması türünü belirten bir URI. WS-Federasyon oturum açma isteği wauth parametre ayarlar. İsteğe bağlı. Varsayılan istekte wauth parametresi dahil edilmediğinden belirtir. boş bir dizedir.|  
|yenilik|İstenen yaş üst sınırını kimlik doğrulama isteklerini, dakikalar içinde. WS-Federasyon oturum açma isteği wfresh parametre ayarlar. İsteğe bağlı. Varsayılan değer sıfırdır. İsteğe bağlı. **Uyarı:**  Sonraki .NET Framework 4.5 sürümünde `freshness` özniteliği, türü olacaktır `xs:string` ve varsayılan değerine `null`.|  
|homeRealm|Ana Bölge kimlik doğrulaması için kullanılacak kimlik sağlayıcısının (IP). WS-Federasyon oturum açma isteği whr parametre ayarlar. İsteğe bağlı. Varsayılan istekte whr parametresi dahil edilmediğinden belirtir. boş bir dizedir.|  
|yayınlayan|Hedeflenen belirteç vericisinin URI. Temel URL, WS-Federasyon oturum açma istekleri ve oturum kapatma istekleri gerekli ayarlar.|  
|persistentCookiesOnPassiveRedirects|Kalıcı tanımlama bilgileri kimlik doğrulaması verilen olup olmadığını belirtir. İsteğe bağlı. Varsayılan "false", tanımlama bilgileri verilmedi.|  
|passiveRedirectEnabled|WSFAM otomatik olarak yetkisiz istekleri bir STS'ye yönlendirmek için etkinleştirilip etkinleştirilmeyeceğini belirtir. İsteğe bağlı. Varsayılan değer "true" ise, yetkisiz istekleri otomatik olarak yönlendirilir.|  
|İlke|Oturum açma isteklerinde kullanmak için uygun ilke konumunu belirten bir URL. Varsayılan değer boş bir dizedir. WS-Federasyon oturum açma isteği wp parametre ayarlar. İsteğe bağlı. Varsayılan istekte wp parametresi dahil edilmediğinden belirtir. boş bir dizedir.|  
|Bölge|İstenen bölge URI'si. (Bağlı olan taraf (RP) güvenlik belirteci hizmeti (STS) tanımlayan bir URI.) İstek wtrealm WS-Federasyon oturum açma isteği parametresi ayarlar. Gerekli.|  
|Yanıtla|Bağlı taraf (RP) uygulaması, güvenlik belirteci hizmeti (STS) gelen yanıtları almak istediğiniz adresini tanımlayan bir URL. WS-Federasyon oturum açma isteği wreply parametre ayarlar. İsteğe bağlı. Varsayılan istekte wreply parametresi dahil edilmediğinden belirtir. boş bir dizedir.|  
|istek|Belirteç verme isteği. WS-Federasyon oturum açma isteği wreq parametre ayarlar. İsteğe bağlı. Varsayılan istekte wreq parametresi dahil edilmediğinden belirtir. boş bir dizedir. Wreq veya wreqptr parametresi istekte içermeden, STS belirteci vermek için hangi tür bilir anlamına gelir.|  
|requestPtr|Belirteç verme isteği konumunu belirten bir URL. İstek wreqptr parametresi ayarlar. İsteğe bağlı. Varsayılan istekte wreqptr parametresi dahil edilmediğinden belirtir. boş bir dizedir. Wreq veya wreqptr parametresi istekte içermeden, STS belirteci vermek için hangi tür bilir anlamına gelir.|  
|requireHttps|Güvenlik belirteci hizmeti (STS) ile iletişim HTTPS protokolünü kullanıp kullanmadığını belirtir. İsteğe bağlı. Varsayılan değer "true" ise, HTTPS kullanılması gerekir.|  
|kaynak|Erişilen, bağlı olan taraf (RP) kaynak olarak tanımlayan bir URI için güvenlik belirteci hizmeti (STS). İsteğe bağlı. WS-Federasyon oturum açma isteği wres parametre ayarlar. İsteğe bağlı. Varsayılan istekte wres parametresi dahil edilmediğinden belirtir. boş bir dizedir. **Not:** wres eski bir parametredir. Belirtin `realm` wtrealm parametresi kullanmayı özniteliği.|  
|signInQueryString|WS-Federasyon oturum açma istek URL'SİNDE uygulama tanımlı sorgu parametreleri belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan ek parametre isteğinde bulunması belirtir. boş bir dizedir. Aşağıdaki biçimi kullanarak bir sorgu dizesi parçası belirtilen parametreler: `"param1=value1&param2=value2&param3=value3"` ve benzeri. **Not:**  Bir yapılandırma dosyasında ' & ", varlık başvurusu kullanarak sorgu dizesindeki karakter belirtilmelidir `&`.|  
|signOutQueryString|WS-Federasyon oturum açma istek URL'SİNDE uygulama tanımlı sorgu parametreleri belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan ek parametre isteğinde bulunması belirtir. boş bir dizedir. Aşağıdaki biçimi kullanarak bir sorgu dizesi parçası belirtilen parametreler: `"param1=value1&param2=value2&param3=value3"` ve benzeri. **Not:**  Bir yapılandırma dosyasında ' & ", varlık başvurusu kullanarak sorgu dizesindeki karakter belirtilmelidir `&`.|  
|signOutReply|Pasif WS-Federation protokolü ile oturum kapatma sırasında istemci güvenlik belirteci hizmeti (STS) tarafından yönlendirilmelidir URL'sini belirtir. Wreply parametresi bir WS-Federasyon oturum kapatma isteği ayarlar. İsteğe bağlı. Varsayılan ek parametre isteğinde bulunması belirtir. boş bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarları içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `<wsFederation>` WSFAM için WS-Federation parametre Varsayılanları ve varsayılan davranışını yapılandırmak için öğesi. WS-Federation parametre ayarları bölümünde tanımlanan `<wsFederation>` öğesi tarafından kullanıma sunulan eşdeğer özelliklerini ayarlama <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı. Bu özellikler WSFAM tarafından verilen her istek için aynı kalır. İstek WSFAM tarafından kullanıma sunulan olayları için olay işleyicileri ekleyerek işleme sırasında WS-Federation parametrelerini dinamik olarak değiştirebilirsiniz; Örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. Daha fazla bilgi için belgelerine bakın <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı.  
  
 `<wsFederation>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.WSFederationElement> sınıfı. Yapılandırma nesnesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> sınıfı. Tek bir <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> örneğine ayarlanır <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> üzerinden erişilen nesne <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği ve WSFAM yapılandırmasını sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<wsFederation>` WSFAM ayarlarını belirten öğe.  
  
> [!WARNING]
>  Bu örnekte, WSFAM, HTTPS kullanmak için gerekli değildir. Bunun nedeni, `requireHttps` özniteliği `<wsFederation>` ayarlanır `false`. Bu ayar, bir güvenlik riski sunabilir gibi çoğu üretim ortamları için önerilmez.  
  
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
