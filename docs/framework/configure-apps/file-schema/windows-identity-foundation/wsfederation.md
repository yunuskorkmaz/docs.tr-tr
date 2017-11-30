---
title: '&lt;wsFederation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e4779baa24e172affad2ed5e04451ad791d7cdf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsfederationgt"></a>&lt;wsFederation&gt;
İçin yapılandırma sağlar <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM).  
  
\<system.identityModel.services >  
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
|authenticationType|Kimlik doğrulama türünü belirten bir URI. WS-Federasyon oturum açma isteği wauth parametresi ayarlar. İsteğe bağlı. Varsayılan wauth parametresi istekte dahil edilmeyen belirtir boş bir dizedir.|  
|yenilik|İstenen en uzun geçerlilik süresi, kimlik doğrulama isteklerinin dakika. WS-Federasyon oturum açma isteği wfresh parametresi ayarlar. İsteğe bağlı. Varsayılan değer sıfırdır. İsteğe bağlı. **Uyarı:** .NET Framework 4.5, sonraki sürümünde `freshness` öznitelik türü olacaktır `xs:string` ve varsayılan değerini `null`.|  
|homeRealm|Kimlik doğrulaması için kullanılacak kimlik sağlayıcısı (IP) giriş bölgesi. WS-Federasyon oturum açma isteği ws parametre ayarlar. İsteğe bağlı. Varsayılan ws parametre istekte dahil edilmeyen belirtir boş bir dizedir.|  
|yayınlayan|Hedeflenen Belirteç Verenin URI'si. Temel URL, WS-Federasyon oturum açma gerekli oturum kapatma isteklerini ve ayarlar.|  
|persistentCookiesOnPassiveRedirects|Kalıcı tanımlama bilgileri kimlik doğrulaması verilen olup olmadığını belirtir. İsteğe bağlı. Varsayılan, "false", tanımlama bilgisi verilmedi.|  
|passiveRedirectEnabled|WSFAM otomatik olarak bir STS yetkisiz isteklerini yeniden yönlendirmek için etkinleştirilip etkinleştirilmeyeceğini belirtir. İsteğe bağlı. Varsayılan değer "true" ise, yetkisiz isteği otomatik olarak yönlendirilir.|  
|İlke|Oturum açma isteklerinde kullanılacak ilgili ilke konumunu belirten bir URL. Varsayılan boş bir dizedir. WS-Federasyon oturum açma isteği wp parametre ayarlar. İsteğe bağlı. Varsayılan wp parametre istekte dahil edilmeyen belirtir boş bir dizedir.|  
|Bölge|İstekte bulunan bölge URI'si. (Bağlı olan taraf (RP) güvenlik belirteci hizmeti (STS) tanımlayan bir URI.) İstek wtrealm WS-Federasyon oturum açma isteği parametresi ayarlar. Gerekli.|  
|Yanıtla|Hangi bağlı olan taraf (RP) uygulama güvenlik belirteci hizmeti (STS) gelen yanıtları almak istediğiniz adres tanımlayan bir URL. WS-Federasyon oturum açma isteği wreply parametresi ayarlar. İsteğe bağlı. Varsayılan wreply parametresi istekte dahil edilmeyen belirtir boş bir dizedir.|  
|istek|Belirteç verme isteği. WS-Federasyon oturum açma isteği wreq parametresi ayarlar. İsteğe bağlı. Varsayılan wreq parametresi istekte dahil edilmeyen belirtir boş bir dizedir. Wreq veya wreqptr parametresi istekte hariç STS belirteci vermek için ne tür bilir anlamına gelir.|  
|requestPtr|Belirteç verme isteğini konumunu belirten bir URL. İstek wreqptr parametresi ayarlar. İsteğe bağlı. Varsayılan wreqptr parametresi istekte dahil edilmeyen belirtir boş bir dizedir. Wreq veya wreqptr parametresi istekte hariç STS belirteci vermek için ne tür bilir anlamına gelir.|  
|requireHttps|Güvenlik belirteci hizmeti (STS) ile iletişim HTTPS protokolünü gerekip gerekmediğini belirtir. İsteğe bağlı. Varsayılan değer "true" ise, HTTPS kullanılması gerekir.|  
|kaynak|Erişilen, kaynak bağlı olan taraf (RP) için tanımlayan bir URI için güvenlik belirteci hizmeti (STS). İsteğe bağlı. WS-Federasyon oturum açma isteği wres parametresi ayarlar. İsteğe bağlı. Varsayılan wres parametresi istekte dahil edilmeyen belirtir boş bir dizedir. **Not:** wres olan eski parametre. Belirtin `realm` özniteliği bunun yerine wtrealm parametresini kullanın.|  
|signInQueryString|WS-Federasyon oturum açma istek URL'SİNDE uygulama tanımlı sorgu parametrelerini belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan ek parametre istekte dahil olduğunu belirten boş bir dizedir. Parametreleri aşağıdaki biçimi kullanarak bir sorgu dizesi parçası belirtilir: `"param1=value1&param2=value2&param3=value3"` ve benzeri. **Not:** yapılandırma dosyasındaki ' & "sorgu dizesi karakter, varlık başvurusunun kullanılarak belirtilmelidir `&`.|  
|signOutQueryString|WS-Federasyon oturum açma istek URL'SİNDE uygulama tanımlı sorgu parametrelerini belirtmek için bir genişletilebilirlik noktası sağlar. İsteğe bağlı. Varsayılan ek parametre istekte dahil olduğunu belirten boş bir dizedir. Parametreleri aşağıdaki biçimi kullanarak bir sorgu dizesi parçası belirtilir: `"param1=value1&param2=value2&param3=value3"` ve benzeri. **Not:** yapılandırma dosyasındaki ' & "sorgu dizesi karakter, varlık başvurusunun kullanılarak belirtilmelidir `&`.|  
|signOutReply|Pasif WS-Federasyon protokolü aracılığıyla oturum kapatma sırasında istemci güvenlik belirteci hizmeti (STS) yeniden yönlendirilmesi gereken URL'yi belirtir. Wreply parametresi bir WS-Federasyon oturum kapatma isteği ayarlar. İsteğe bağlı. Varsayılan ek parametre istekte dahil olduğunu belirten boş bir dizedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Federationconfiguration'a >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|Yapılandırma ayarlarını içeren <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) ve <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `<wsFederation>` WS-Federasyon parametre Varsayılanları ve varsayılan davranışı WSFAM için yapılandırma öğesi. WS-Federasyon parametre ayarları altında tanımlanan `<wsFederation>` öğesi tarafından sunulan eşdeğer özelliklerini ayarlama <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı. Bu özellikleri WSFAM tarafından verilen her istek için aynı kalır. İstek WSFAM tarafından kullanıma sunulan olayları için olay işleyicileri ekleyerek işleme sırasında WS-Federasyon parametrelerini dinamik olarak değiştirebilirsiniz; Örneğin, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider> olay. Daha fazla bilgi için belgelerine bakın <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı.  
  
 `<wsFederation>` Öğesi ile temsil edilir <xref:System.IdentityModel.Services.Configuration.WSFederationElement> sınıfı. Yapılandırma nesnesi tarafından temsil edilen <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> sınıfı. Tek bir <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration> örneği ayarlanmış <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> üzerinden erişilen nesne <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> özelliği ve WSFAM için yapılandırmasını sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML gösterildiği bir `<wsFederation>` öğesi WSFAM ayarlarını belirtir.  
  
> [!WARNING]
>  Bu örnekte, WSFAM, HTTPS kullanmak üzere gerekli değildir. Bunun nedeni, `requireHttps` özniteliği `<wsFederation>` öğesi ayarlanmış `false`. Bu ayar bir güvenlik riski sayılabilir çoğu üretim ortamları için önerilmez.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
