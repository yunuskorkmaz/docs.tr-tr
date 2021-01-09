---
title: gcAllowVeryLargeObjects öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058135"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects> öğesi

64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a>Öznitelikler
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
### <a name="enabled-attribute"></a>enabled özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Toplam boyutu 2 GB'den büyük diziler etkin değildir. Bu varsayılan seçenektir.|  
|`true`|Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.|  
  
## <a name="child-elements"></a>Alt öğeleri  

Yok.  
  
## <a name="parent-elements"></a>Üst öğeler
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:  
  
- Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
- Tek boyuttaki maksimum boyut, bayt dizileri ve tek baytlık yapıların dizileri için 2.147.483.591 (0x7FFFFFC7) ve diğer türleri içeren diziler için 2.146.435.071 (0X7FEFFFFF).  
  
- Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.  
  
> [!CAUTION]
> Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun. Örneğin, arabellekler olarak dizileri kullanan güvenli olmayan kod, dizilerin 2 GB 'ı aşmaması durumunda yazılmışsa arabellek taşmalarına açıktır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>Destekleyen:

.NET Framework 4,5 ve sonraki sürümler

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
