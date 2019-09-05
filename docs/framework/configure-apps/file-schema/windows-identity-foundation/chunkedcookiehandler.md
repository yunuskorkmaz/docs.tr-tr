---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252102"
---
# <a name="chunkedcookiehandler"></a>\<Öbek için yığın tanımlama >
Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Tanımlama, ıehandler >** ](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Öbek için yığın tanımlama >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Öbek boyutu|Herhangi bir HTTP tanımlama bilgisinin HTTP tanımlama bilgisi verilerinin karakter cinsinden en büyük boyutu. Öbek boyutunu ayarlarken dikkatli olmanız gerekir. Web tarayıcıları, her etki alanı için izin verilen tanımlama bilgileri ve sayı boyutları için farklı sınırlara sahiptir. Örneğin, özgün Netscape belirtimi bu sınırları ifade etmek için: 300 tanımlama bilgileri toplamı, tanımlama bilgisi üst bilgisi başına 4096 bayt (meta veriler, yalnızca tanımlama bilgisi değeri değil) ve etki alanı başına 20 tanımlama bilgisi. Varsayılan değer 2000 ' dir. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Tanımlama, ıehandler >](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> (Sam)tanımlamabilgileriniokumakveyazmak<xref:System.IdentityModel.Services.SessionAuthenticationModule> için kullandığı öğesini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğesinin özniteliğini "varsayılan" veya "öbekli" olarak <xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` ayarlayarak belirttiğinizde, tanımlama bilgisi işleyicisinin bir `<chunkedCookieHandler>` alt öğe ekleyerek tanımlama bilgilerini okumak ve yazmak için kullandığı öbek boyutunu belirtebilirsiniz. `<cookieHandler>` `chunkSize` özniteliği ayarlanıyor. `<chunkedCookieHandler>` Öğe yoksa, 2000 baytlık varsayılan öbek boyutu kullanılır. `mode` Öznitelik "Custom" olarak ayarlandığında bu öğe belirtilemez.  
  
 `<chunkedCookieHandler>` Öğesi sınıfı<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> tarafından temsil edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 3000 baytlık öbeklere tanımlama bilgilerini yazan bir öbekli tanımlama bilgisi işleyicisini yapılandırır.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
