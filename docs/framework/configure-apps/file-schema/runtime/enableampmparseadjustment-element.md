---
title: "&lt;EnableAmPmParseAdjustment&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed01035d7d5b154ebc6541eb6ac3dbae6a413fbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; öğesi
Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi gün, ay, saat ve AM/PM Belirleyicisi içeren tarih dizeleri ayrıştırmak için kullanıp kullanmayacağınızı belirler.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Tarih ve saat yöntemleri ayrıştırma ayarlanmış bir kural kümesi yalnızca bir gün, ay, saat ve AM/PM Belirleyicisi içeren tarih dizeleri ayrıştırma için olup olmadığını belirtir.|  
  
### <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Tarih ve saat yöntemleri ayrıştırma ayarlanmış kuralları yalnızca bir gün, ay, saat ve AM/PM Belirleyicisi içeren tarih dizeleri ayrıştırma için kullanmayın.|  
|1.|Tarih ve saat yöntemleri ayrıştırma yalnızca bir gün, ay, saat ve AM/PM Belirleyicisi içeren tarih dizeleri ayrıştırma için ayarlanan kurallarını kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<EnableAmPmParseAdjustment>` Öğesi denetimleri nasıl aşağıdaki yöntemlerden bir sayısal gün ve saatte bir ve AM/PM Belirleyicisi (örneğin, "4/10 6 AM") ve ardından ay içeren bir tarih dizesi ayrıştırılamıyor:  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Herhangi bir desen etkilenir.  
  
 `<EnableAmPmParseAdjustment>` Öğesi hiçbir etkisi vardır <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> yöntemleri.  
  
> [!IMPORTANT]
>  .NET Core ve .NET yerel, ayarlanan AM/PM ayrıştırma kurallar varsayılan olarak etkinleştirilir.  
  
 Ayrıştırma ayarlama kuralı etkin değilse, dizenin ilk rakam 12 saat saat yorumlanır ve AM/PM Belirleyicisi dışında dizesindeki kalanı göz ardı edilir. Ayrıştırma yöntemi tarafından döndürülen saat ve tarihi geçerli tarih ve saat tarih dizesi ayıklanan oluşur.  
  
 Yöntemi ayrıştırılırken ayrıştırma ayarlama kuralı etkinleştirilirse, geçerli yıl ait olarak ay ve gün yorumlanacağı ve 12 saatlik saatlik sürede yorumlayamadı.  
  
 Aşağıdaki tabloda fark gösterilmektedir <xref:System.DateTime> değeri <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> yöntemi dizesini ayrıştırmak için kullanılan "" 4/10 6 AM"ile `<EnableAmPmParseAdjustment>` öğenin `enabled` özelliği"0"veya"1"olarak ayarlanmış. Bugünün tarihi 5 Ocak 2017 olduğunu ve belirtilen kültürün "G" biçim dizesi kullanılarak biçimlendirilmiş olması gibi tarihi görüntüler olduğunu varsayar.  
  
|Kültür adı|Etkin = "0"|Etkin = "1"|  
|------------------|------------------|------------------|  
|en-US|5/1/2017 4:00:00 AM|4/10/2017 6:00:00 AM|  
|tr GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<çalışma zamanı > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<Yapılandırma > öğesi](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
