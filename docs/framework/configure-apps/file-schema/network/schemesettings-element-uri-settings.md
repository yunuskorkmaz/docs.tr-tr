---
title: "&lt;schemeSettings&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4cf1d2013a51985f9d7772ac0ef86e5dbb120be9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltschemesettingsgt-element-uri-settings"></a>&lt;schemeSettings&gt; öğesi (URI ayarları)
Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.  
  
 \<Yapılandırma >  
\<URI >  
\<schemeSettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[ekleme](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|Düzen adı için bir düzeni ayarı ekler.|  
|[Temizle](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|Tüm mevcut düzeni ayarlarını temizler.|  
|[Kaldır](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|Düzen adı için bir düzeni ayarı kaldırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|**Öğesi**|**Açıklama**|  
|-----------------|---------------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.Uri?displayProperty=nameWithType> sınıfı kaydını çıkışları yüzde yolu sıkıştırma yürütmeden önce yolu ayırıcısı kodlanmış. Bu, aşağıdaki gibi saldırılarına karşı bir güvenlik mekanizması olarak kullanılmıştır:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu URI aktarılırsa modülleri aşağıya doğru yüzde işlenmemesinin karakterlerin doğru kodlanmış, sunucu tarafından yürütülen aşağıdaki komutta neden olabilir:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Bu nedenle, <xref:System.Uri?displayProperty=nameWithType> sınıfı ilk kaydını çıkışları yol ayırıcısı ve yol sıkıştırma uygular. Yukarıdaki kötü amaçlı URL'sine geçirme sonucunu <xref:System.Uri?displayProperty=nameWithType> sınıfı aşağıdaki URI Oluşturucusu sonuçlanır:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Bu varsayılan davranışı değil, özel şema için schemeSettings yapılandırma seçeneğini kullanarak kaldırın kaçış yüzde kodlanmış yolu sınırlayıcıları için değiştirilebilir.  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  
 Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> http şeması için yüzde olarak kodlanmış yol ayırıcısı kaçış değil desteklemek için sınıf.  
  
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
|Şema adı||  
|Dosya doğrulama||  
|Boş olabilir.||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
