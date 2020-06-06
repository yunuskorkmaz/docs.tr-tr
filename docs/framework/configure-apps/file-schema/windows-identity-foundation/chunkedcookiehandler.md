---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252102"
---
# \<chunkedCookieHandler>
Öğesini yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Bu öğe yalnızca `mode` `<cookieHandler>` öğenin özniteliği "default" veya "öbekli" ise bulunabilir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
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
|Öbek boyutu|Herhangi bir HTTP tanımlama bilgisinin HTTP tanımlama bilgisi verilerinin karakter cinsinden en büyük boyutu. Öbek boyutunu ayarlarken dikkatli olmanız gerekir. Web tarayıcıları, her etki alanı için izin verilen tanımlama bilgileri ve sayı boyutları için farklı sınırlara sahiptir. Örneğin, özgün Netscape belirtimi bu limitleri sınırlar: 300 tanımlama bilgileri toplamı, tanımlama bilgisi üstbilgisi başına 4096 bayt (meta veriler dahil, yalnızca tanımlama bilgisi değerini değil) ve etki alanı başına 20 tanımlama bilgisi. Varsayılan değer 2000’dir. Gereklidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) tanımlama bilgilerini okumak ve yazmak için kullandığı öğesini yapılandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` `<cookieHandler>` Öğesinin özniteliğini "varsayılan" veya "öbekli" olarak ayarlayarak belirttiğinizde, tanımlama bilgisi işleyicisinin bir `<chunkedCookieHandler>` alt öğe ekleyerek ve özniteliğini ayarlayarak tanımlama bilgilerini okumak ve yazmak için kullandığı öbek boyutunu belirtebilirsiniz `chunkSize` . `<chunkedCookieHandler>`Öğe yoksa, 2000 baytlık varsayılan öbek boyutu kullanılır. `mode`Öznitelik "Custom" olarak ayarlandığında bu öğe belirtilemez.  
  
 `<chunkedCookieHandler>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 3000 baytlık öbeklere tanımlama bilgilerini yazan bir öbekli tanımlama bilgisi işleyicisini yapılandırır.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
