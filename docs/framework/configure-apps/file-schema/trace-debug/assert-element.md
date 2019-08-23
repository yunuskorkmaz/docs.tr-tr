---
title: <assert> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927192"
---
# <a name="assert-element"></a>\<onaylama > öğesi
<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<onaylama >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`assertuienabled`|İsteğe bağlı öznitelik.<br /><br /> **Debug. onaylama** yöntemi **false**olarak değerlendirilirse bir ileti kutusu görüntülenip görüntülenmeyeceğini belirtir.|  
|`logfilename`|İsteğe bağlı öznitelik.<br /><br /> **Hata ayıkla. onaylama** **yanlış**olarak değerlendirilirse iletinin yazılacağı dosyanın adını belirtir.|  
  
## <a name="assertuienabled-attribute"></a>AssertUiEnabled özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|İleti kutusunu görüntüler. Bu varsayılandır.|  
|`false`|İleti kutusunu görüntülemez.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Onaylama > öğesindeki her iki öznitelik  **\<** de isteğe bağlıdır. İletileri yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutularından etkin bırakarak mesaj yazılacak bir dosya belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, **hata ayıklama. onayı** çağırdığınızda ileti kutularının nasıl devre dışı bırakılacağını gösterir ve iletileri öğesine `c:\log.txt`yazın.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
