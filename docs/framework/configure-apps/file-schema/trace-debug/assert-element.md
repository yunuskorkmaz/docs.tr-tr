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
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088943"
---
# <a name="assert-element"></a>\<onaylama > öğesi
<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.  

[ **\<configuration >** ](../configuration-element.md) \
[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp; **\<onaylama >**

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
 Her iki öznitelik de **\<onaylama >** öğesi isteğe bağlıdır. İletileri yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutularından etkin bırakarak mesaj yazılacak bir dosya belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, **hata ayıklama. onaylama** yöntemini çağırdığınızda ileti kutularının görüntülenmesine nasıl devre dışı bırakılacağını gösterir ve `c:\log.txt`iletileri yazın.  
  
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
