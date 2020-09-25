---
title: <EnableAmPmParseAdjustment> Öğesi
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167242"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment> Öğesi

Tarih ve saat ayrıştırma yöntemlerinin, gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirtir.|  
  
### <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanmaz.|  
|1|Tarih ve saat ayrıştırma yöntemleri yalnızca gün, ay, saat ve PM/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanan kuralları kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<EnableAmPmParseAdjustment>`Öğesi, aşağıdaki yöntemlerin sayısal bir gün ve ay içeren bir tarih dizesini nasıl ayrıştırarak bir saat ve bır har/PM göstergesini ("4/10 6" gibi) denetler:  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Başka desenler etkilenmemiştir.  
  
 `<EnableAmPmParseAdjustment>`Öğesinin <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> ,, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri üzerinde hiçbir etkisi yoktur.  
  
> [!IMPORTANT]
> .NET Core ve .NET Native 'de, ayarlanan saat/PM ayrıştırma kuralları varsayılan olarak etkindir.  
  
 Ayrıştırma ayarlama kuralı etkinleştirilmemişse, dizenin ilk basamak, 12 saatlik saatin saati olarak yorumlanır ve bu dizenin geri kalanı, ı/PM göstergesi hariç sayılır. Ayrıştırma yöntemi tarafından döndürülen tarih ve saat, geçerli tarih ve Tarih dizesinden çıkarılan günün saati içerir.  
  
 Ayrıştırma ayarlama kuralı etkinleştirilirse, ayrıştırma yöntemi geçerli yıla ait günü ve ayı yorumlayıp saati 12 saatlik saatin saati olarak yorumlar.  
  
 Aşağıdaki tabloda, <xref:System.DateTime> <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> yöntemi " `<EnableAmPmParseAdjustment>` `enabled` 0" veya "1" olarak ayarlanan öğenin özelliği Ile "" 4/10 6 har "dizesini ayrıştırmak için kullanılan değerin farkı gösterilmektedir. Bugünün tarihinin 5 Ocak 2017 olduğunu varsayar ve belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilip biçimlendirildiğine ilişkin tarihi görüntüler.  
  
|Kültür adı|etkin = "0"|etkin = "1"|  
|------------------|------------------|------------------|  
|tr-TR|1/5/2017 4:00:00|4/10/2017 6:00:00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<runtime> Dosyalarında](runtime-element.md)
- [\<configuration> Dosyalarında](../configuration-element.md)
