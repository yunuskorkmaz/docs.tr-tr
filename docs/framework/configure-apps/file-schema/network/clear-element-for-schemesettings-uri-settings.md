---
title: schemeSettings için <clear> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 17069a56a8647871e98d70826a97a8fe407a0887
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205067"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a>schemeSettings için \<clear> Öğesi (Uri Ayarları)

Varolan tüm düzen ayarlarını temizler.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Syntax  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<schemeSettings> Öğesi (URI ayarları)](schemesettings-element-uri-settings.md)|<xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı yol sıkıştırmayı yürütmeden önce, yüzde olarak kodlanmış yol sınırlayıcılarını kaldırır. Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu URI, yüzde kodlamalı karakterleri doğru şekilde işlemeyen modüllere geçiriliyorsa, aşağıdaki komut sunucu tarafından yürütülebilmesiyle sonuçlanabilir:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk olarak yol sınırlayıcılarını iptal eder ve yol sıkıştırması uygular. Yukarıdaki kötü amaçlı URL 'YI sınıf oluşturucusuna geçirmenin sonucu <xref:System.Uri?displayProperty=nameWithType> AŞAĞıDAKI URI ile sonuçlanır:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu varsayılan davranış, belirli bir düzen için ıgmesettings yapılandırma seçeneği kullanılarak yüzde olmayan kodlanmış yol sınırlayıcılarını kaçırılmamış şekilde değiştirilebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Uri> tüm düzen ayarlarını temizleyen sınıf tarafından kullanılan bir yapılandırmayı gösterir ve ardından http şeması için tam olmayan yüzde kodlamalı yol sınırlayıcıları için destek ekler.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
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
- [Ağ ayarları şeması](index.md)
