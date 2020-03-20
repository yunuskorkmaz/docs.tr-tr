---
title: <schemeSettings> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154653"
---
# <a name="schemesettings-element-uri-settings"></a>\<şemaAyarları> Öğesi (Uri Ayarları)
Belirli düzenler için <xref:System.Uri> a'nın nasıl ayrıştırılacağını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<şemaAyarlar>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 None  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Ekle](add-element-for-schemesettings-uri-settings.md)|Şema adı için düzen ayarı ekler.|  
|[Temizleyin](clear-element-for-schemesettings-uri-settings.md)|Varolan tüm düzen ayarlarını temizler.|  
|[Kaldırmak](remove-element-for-schemesettings-uri-settings.md)|Düzen adı için düzen ayarını kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğe**|**Açıklama**|  
|-----------------|---------------------|  
|[Urı](uri-element-uri-settings.md)|.NET Framework'ün tek düzen kaynak tanımlayıcıları (URI) kullanılarak ifade edilen web adreslerini nasıl işleyeceğini belirten ayarlar içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıf yol sıkıştırma yürütmeden önce yüzde kodlanmış yol sınırlayıcıları kaçar. Bu, aşağıdaki gibi saldırılara karşı bir güvenlik mekanizması olarak uygulanmıştır:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu URI, yüzde kodlanmış karakterleri doğru işlemeyan modüllere aktarılırsa, sunucu tarafından aşağıdaki komutun yürütülmesine neden olabilir:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıf ilk un-escapes yol sınırlayıcılar ve daha sonra yol sıkıştırma uygular. Yukarıdaki kötü amaçlı URL'yi <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturucuya geçirmenin sonucu aşağıdaki URI ile sonuçlanır:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu varsayılan davranış, belirli bir düzen için düzenAyarlar yapılandırma seçeneğini kullanarak kodlanmış yol sınırçözücülerini kaldırmamak için değiştirilebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Uri> sınıf tarafından http düzeni için yüzde kodlanmış yol sınır çözücülerden kaçmayan desteği için kullanılan bir yapılandırmayı gösterir.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>Öğe Bilgisi  
  
|||
|-|-|  
|Ad Alanı|Sistem|  
|Şema Adı||  
|Doğrulama Dosyası||  
|Boş Olabilir||  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](index.md)
