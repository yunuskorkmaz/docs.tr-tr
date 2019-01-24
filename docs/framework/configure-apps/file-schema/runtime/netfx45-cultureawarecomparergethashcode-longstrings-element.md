---
title: '&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67dae26733527a85f4fc13734da896193e53db8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576895"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi
Çalışma zamanı için karma kodları hesaplamak üzere sabit miktarda bellek kullanıp kullanmayacağını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
<NetFx45_CultureAwareComparerGetHashCode_LongStrings>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Ortak dil çalışma zamanı değişken miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak üzere yöntemi. Bu varsayılandır.|  
|1.|Ortak dil çalışma zamanı sabit miktarda bellek ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodları hesaplamak üzere yöntemi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, ortak dil çalışma zamanı değişken miktarda bellek ayırır. <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi ve bir <xref:System.ArgumentException> yöntem çok büyük dizelerin karma kodunu (birkaç milyon karakterden uzun) hesaplamayı denediğinde oluşturulur. Bu öğe bir uygulama yapılandırma dosyası ve ayarı ekleyerek, `enabled` özniteliğini "1", şu belirtebilirsiniz <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi, karma kodları hesaplama için sabit miktarda bellek ayıran başka bir algoritma kullanın.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Öğesi kullanılmaz [!INCLUDE[win8](../../../../../includes/win8-md.md)] ve sonraki sürümler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
