---
title: <EnableAmPmParseAdjustment> Öğesi
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d1a14199debbb90827c1ea95347d485a636329
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704849"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment > öğesi
Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirler.  
  
 \<Yapılandırma >  
 \<çalışma zamanı >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırılacak kullanıp kullanmadığını belirtir.|  
  
### <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Tarih ve saat yöntemleri ayrıştırma düzeltilen kurallar yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırma için kullanmayın.|  
|1.|Tarih ve saat yöntemleri ayrıştırma yalnızca bir gün, ay, saat ve AM/PM göstergesi içeren tarih dizeleri ayrıştırma için ayarlanmış kuralları kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<EnableAmPmParseAdjustment>` Öğe denetimleri nasıl aşağıdaki yöntemlerden bir sayısal günlük ve aylık bir saat ve bir AM/PM göstergesi (örneğin, "4/10 6 AM") içeren bir tarih dizesi ayrıştırılamıyor:  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Herhangi bir desen etkilenir.  
  
 `<EnableAmPmParseAdjustment>` Öğesi hiçbir etkiye sahiptir <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri.  
  
> [!IMPORTANT]
>  .NET Core ve .NET Native, ayarlanan AM/PM ayrıştırma kurallarını varsayılan olarak etkindir.  
  
 Ayrıştırma ayarlama kuralı etkin değilse, dizenin ilk basamak 12 saatlik düzende saatlik yorumlanır ve AM/PM göstergesi dışında dizenin geri kalanı göz ardı edilir. Ayrıştırma yöntem tarafından döndürülen saat ve tarihi geçerli tarih ve saat ve tarih dizesindeki ayıklanan oluşur.  
  
 Yöntemi ayrıştırma ayrıştırma ayarlama kuralı etkinleştirilirse, ait geçerli yıl, ay ve günü yorumlar ve saati 12 saatlik düzende saatlik olarak yorumlayın.  
  
 Aşağıdaki tabloda, fark gösterilmektedir <xref:System.DateTime> değeri <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> dizeyi ayrıştırmak için kullanılan yöntemi "" 4/10 6 AM"ile `<EnableAmPmParseAdjustment>` öğenin `enabled` özelliği"0"veya"1"olarak ayarlayın. Bu, bugünün tarihi 5 Ocak 2017 ve gibi belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilir tarihi görüntüler varsayar.  
  
|Kültür adı|Etkin = "0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|1/5/2017 4:00: 00'DA|4/10/2017 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<çalışma zamanı > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
