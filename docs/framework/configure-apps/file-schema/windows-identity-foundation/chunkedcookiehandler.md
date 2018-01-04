---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c5d526ccd48ea5e822d5d29fb38dacd895c2556c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Yapılandırır <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Bu öğe yalnızca mevcut olabilir, `mode` özniteliği `<cookieHandler>` öğesidir "Varsayılan" veya "Öbekli".  
  
 \<system.identityModel.services >  
\<Federationconfiguration'a >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
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
|chunkSize|Karakterleri, herhangi bir HTTP tanımlama bilgisi HTTP tanımlama bilgisi verileri, en büyük boyutu. Öbek boyutu ayarlarken dikkatli olmanız gerekir. Web tarayıcıları farklı sınırlara tanımlama bilgileri ve etki alanı başına izin verilen sayıyı boyutuna sahiptir. Örneğin, özgün Netscape belirtiminin bu sınırları belirlenen: 300 tanımlama bilgilerini toplam, 4096 bayt tanımlama bilgisi üstbilgisi (meta verileri, yalnızca tanımlama bilgisi değeri dahil) ve etki alanı başına 20 tanımlama bilgisi. Varsayılan değer 2000'dir. Gerekli.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Yapılandırır <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) okuma ve yazma tanımlama için kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Belirttiğinizde bir <xref:System.IdentityModel.Services.ChunkedCookieHandler> ayarlayarak `mode` özniteliği `<cookieHandler>` "Varsayılan" veya "Chunked" öğesine, tanımlama bilgisi işleyici okumak ve tanımlama bilgileri dahil ederek yazmak için kullandığı öbek boyutu belirtebilirsiniz bir `<chunkedCookieHandler>` alt öğesi ve ayarlama, `chunkSize` özniteliği. Varsa `<chunkedCookieHandler>` öğesi mevcut değil, 2000 bayt varsayılan öbek boyutu kullanılır. Bu öğe olamaz belirtilen `mode` özniteliği "Özel" olarak ayarlanmış.  
  
 `<chunkedCookieHandler>` Öğesi ile temsil edilir <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek 3000 bayt yığınlar halinde tanımlama bilgilerini yazar parçalı tanımlama bilgileri işleyici yapılandırır.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
