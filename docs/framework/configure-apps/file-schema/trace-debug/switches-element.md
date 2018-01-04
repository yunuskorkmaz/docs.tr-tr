---
title: "&lt;anahtarlar&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64cf3ba9e5529c4a46b2d5365931a47ad2ab211a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltswitchesgt-element"></a>&lt;anahtarlar&gt; öğesi
İzleme anahtarları ve izleme anahtarları belirlendiği düzeyi içerir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<anahtarları >  
  
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
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|İzleme anahtarı ayarlandığı düzeyini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`System.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yapılandırma dosyasında koyarak izleme anahtarı düzeyini değiştirebilirsiniz. Anahtar ise bir <xref:System.Diagnostics.BooleanSwitch>açıp kapatabilirsiniz. Anahtar ise bir <xref:System.Diagnostics.TraceSwitch>, izleme türlerini belirtmek için farklı düzeyleri atayabilir veya hata ayıklama iletileri uygulama çıkarır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<geçiş >** ayarlamak için öğenin `General` izleme anahtara <xref:System.Diagnostics.TraceLevel> düzey ve etkinleştirme `Data` Boolean izleme anahtarı.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
