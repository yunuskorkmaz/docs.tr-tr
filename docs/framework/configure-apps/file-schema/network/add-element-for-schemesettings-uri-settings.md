---
title: schemeSettings için <add> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087712"
---
# <a name="add-element-for-schemesettings-uri-settings"></a>\<için > öğesi ekleme (Uri Ayarları)
Düzen adı için bir düzen ayarı ekler.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<urı >** ](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları**](schemesettings-element-uri-settings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bu ayarın geçerli olduğu Düzen adı. Yalnızca Name = "http" ve Name = "https" değerleri desteklenir.|  
  
## <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|genericUriParserOptions|Bu şema için ayrıştırıcı seçenekleri. Yalnızca genericUriParserOptions = "DontUnescapePathDotsAndSlashes" değeri desteklenir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<düzeni > öğesi (URI ayarları)](schemesettings-element-uri-settings.md)|Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılagösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı, yol sıkıştırmayı yürütmeden önce yüzde kodlamalı yol sınırlayıcılarını kaldırır. Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk olarak yol sınırlayıcılarını kaldırın ve ardından yol sıkıştırması uygular. Yukarıdaki kötü amaçlı URL 'YI <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucusuna geçirmenin sonucu aşağıdaki URI ile sonuçlanır:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, http şemasına yönelik yüzde kodlamalı yol sınırlayıcılarını yok etmek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırmayı gösterir.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
