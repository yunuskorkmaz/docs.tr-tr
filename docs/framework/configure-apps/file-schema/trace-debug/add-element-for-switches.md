---
title: <add> öğe için <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120100"
---
# <a name="add-element-for-switches"></a>\<Ekle > öğesi için \<anahtarlar >
Bir izleme anahtarı ayarlandığı düzeyini belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<anahtarlar >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**name**|Gerekli öznitelik.<br /><br /> Anahtar adını belirtir. Bu özniteliğin değeri karşılık gelen *displayName* Oluşturucusu geçiş yapmak için geçirilen parametre.|  
|**value**|Gerekli öznitelik.<br /><br /> Anahtar düzeyini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`switches`|İzleme anahtarları ve izleme anahtarları ayarlandığı düzeyi içerir.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yapılandırma dosyasına koyarak, bir izleme anahtarı düzeyini değiştirebilirsiniz. Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz. Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>hata ayıklama iletileri uygulama çıkışları veya izleme türlerini belirtmek için farklı düzeylerde atayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<Ekle >** ayarlanacak öğenin `General` izleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyi ve etkinleştirme `Data` Boole izleme anahtarı.  
  
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
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
