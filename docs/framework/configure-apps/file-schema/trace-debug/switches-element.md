---
title: <switches> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153236"
---
# <a name="switches-element"></a>\<anahtarları> Eleman
İzleme anahtarları ve izleme anahtarlarının ayarlandığı düzeyi içerir.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<anahtarları>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<>ekleyin](add-element-for-switches.md)|İzleme anahtarının ayarlandığı düzeyi belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`System.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yapılandırma dosyasına koyarak izleme anahtarıdüzeyini değiştirebilirsiniz. Anahtar bir <xref:System.Diagnostics.BooleanSwitch>ise, açıp kapatabilirsiniz. Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulama çıktılarının izleme veya hata ayıklama iletilerinin türlerini belirtmek için bu düzeylere farklı düzeyler atayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, izleme anahtarını `General` <xref:System.Diagnostics.TraceLevel> düzeye ayarlamak ve Boolean izleme `Data` anahtarını ** \<** etkinleştirmek için anahtar>öğesinin nasıl kullanılacağı gösterilmektedir.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
