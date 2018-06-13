---
title: '&lt;TimeSpan_LegacyFormatMode&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0faf2876680ef5ec3fc7373cae9f81eb091f47a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753976"
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;TimeSpan_LegacyFormatMode&gt; öğesi
Çalışma zamanı işlemleriyle biçimlendirmesindeki eski davranışı korur olup olmadığını belirler <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
< TimeSpan_LegacyFormatMode >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı ile eski biçimlendirme davranışı kullanıp kullanmadığını belirtir <xref:System.TimeSpan?displayProperty=nameWithType> değerleri.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı eski biçimlendirme davranışı geri yüklemeyin.|  
|`true`|Çalışma zamanı eski biçimlendirme davranışını geri yükler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> Implements yapısı <xref:System.IFormattable> arabirimi ve standart ve özel biçim dizeleri işlemleriyle biçimlendirmeyi destekler. Desteklenmeyen Biçim belirticisi veya biçim dizesini ayrıştırma yönteminin karşılaştığında oluşturur bir <xref:System.FormatException>.  
  
 .NET Framework'ün önceki sürümlerinde <xref:System.TimeSpan> uygulamaz yapısı <xref:System.IFormattable> ve biçim dizeleri desteklememektedir. Bununla birlikte, çoğu geliştiricinin yanlışlıkla kabul, <xref:System.TimeSpan> biçim dizeleri kümesi desteklemediği ve bunların içinde kullanılan [bileşik işlemleri biçimlendirme](../../../../../docs/standard/base-types/composite-formatting.md) gibi yöntemleriyle <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalde, bir tür uyguluyorsa <xref:System.IFormattable> ve destekler biçim dizeleri, dizeler genellikle throw yöntemleri desteklenmeyen biçim çağrıları bir <xref:System.FormatException>. Ancak, çünkü <xref:System.TimeSpan> uygulamaz <xref:System.IFormattable>, çalışma zamanı biçim dizesi yoksayıldı ve bunun yerine adlı <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi. Biçim dizeleri biçimlendirme işlemi üzerinde hiçbir etkisi olan karşın, bunların varlığı içinde sonucu oluşmadıysa, yani bir <xref:System.FormatException>.  
  
 Eski kod iletir bir bileşik yöntemi ve geçersiz biçim dizesi biçimlendirme ve kodun yeniden derlenmesi durumlarda, kullandığınız `<TimeSpan_LegacyFormatMode>` eski geri yüklemek için öğesi <xref:System.TimeSpan> davranışı. Ayarladığınızda `enabled` özniteliği bu öğenin `true`, bileşik bir çağrı yöntemi sonuçlarında biçimlendirme <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yerine <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>ve bir <xref:System.FormatException> değil atılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek başlatır bir <xref:System.TimeSpan> nesne ve ile biçimlendirmeniz girişimleri <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> desteklenmeyen standart biçim dizesini kullanarak yöntemi.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Örnek çalıştırdığınızda [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] veya önceki bir sürümünde aşağıdaki çıkış gösterir:  
  
```  
12:30:45  
```  
  
 Örnek çalıştırırsanız, bu belirtmeyecektir çıktısını farklıdır [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] veya sonraki sürümü:  
  
```  
Invalid Format  
```  
  
 Ancak, örneği aşağıdaki yapılandırma dosyası eklerseniz, dizin adı ve örnek sonra çalıştıracağınız [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] veya sonraki bir sürümü çıktı çalışırken örnek tarafından üretilen özdeş [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
