---
title: schemeSettings için <clear> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 5bb97fbe04cbd3bba85113200abe6495639bab87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287111"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a>\<Temizle > öğesi (Uri ayarları) schemeSettings için
Tüm mevcut düzeni ayarlarını temizler.  
  
 \<Yapılandırma >  
\<URI >  
\<schemeSettings >  
\<Temizleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|[\<schemeSettings > öğesi (Uri ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Belirtir nasıl bir <xref:System.Uri> belirli düzenleri için ayrıştırılacak.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı Geri Al çıkışları yüzde yolu sınırlayıcı yolu sıkıştırma yürütmeden önce kodlanmış. Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak uygulanmıştır:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu URI iletilir aşağı modülleri yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından çalıştırılan aşağıdaki komutu neden:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk geri al çıkışları yol ayırıcıları ve yol sıkıştırma uygular. Yukarıda kötü amaçlı URL'sini geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucu sonuçları aşağıdaki URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu varsayılan davranışı değil, için belirli bir düzeni schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcılar için değiştirilebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> sınıfı, tüm düzeni ayarlarını temizler ve ardından http düzeni için yol yüzde olarak kodlanmış sınırlayıcılar kaçış değil desteği ekler.  
  
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
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
