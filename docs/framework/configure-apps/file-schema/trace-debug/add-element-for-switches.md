---
title: <switches> için <add> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 8fcd5cbe63a323a7509f5ff8c615364295c244d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920555"
---
# <a name="add-element-for-switches"></a>\<Anahtarlar için \<> öğesi ekleme >
Bir izleme anahtarının ayarlandığı düzeyi belirtir.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<Anahtarlar >  
\<> Ekle  
  
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
|**name**|Gerekli öznitelik.<br /><br /> Anahtarın adını belirtir. Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.|  
|**value**|Gerekli öznitelik.<br /><br /> Anahtar düzeyini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`switches`|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz. Anahtar bir <xref:System.Diagnostics.BooleanSwitch>ise, açıp kapatabilirsiniz. Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek,  **\<Add >** `General` öğesinin, izleme anahtarını <xref:System.Diagnostics.TraceLevel> düzeye ayarlamak için nasıl kullanılacağını gösterir ve `Data` Boole izleme anahtarını etkinleştirir.  
  
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
