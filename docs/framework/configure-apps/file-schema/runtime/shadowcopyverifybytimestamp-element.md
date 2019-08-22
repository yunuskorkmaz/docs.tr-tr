---
title: <shadowCopyVerifyByTimestamp> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3ea57364832553d16c7e34fc887b1c9f821602
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663444"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp > öğesi
Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<shadowCopyVerifyByTimestamp > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|etkinletir|Gerekli öznitelik.<br /><br /> Derlemeyi gölge kopyalamadan önce bir derlemenin güncelleştirilip güncelleştirilmediğini anlamak için, gölge kopyalamayı kullanan uygulama etki alanlarının derleme zaman damgalarını karşılaştırın.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Başlangıçta, yalnızca gölge kopya dizinine son kopyalandıklarından bu yana güncelleştirilmiş derlemeleri kopyalar. .NET Framework 4 için varsayılan değer budur.|  
|false|Başlangıçtaki tüm dosyaları kopyalamak için .NET Framework önceki sürümlerinin başlangıç davranışına geri döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 ' te başlayarak, derlemeler yalnızca, zaman damgaları, gölge kopya dizinine en son kopyalandıklarından bu yana değiştirildikleri belirtilmişse gölge olarak kopyalanır. Bu, gölge kopyalama [derlemeler](../../../app-domains/shadow-copy-assemblies.md)' de açıklandığı gibi, gölge kopyalamayı kullanan birçok uygulama için başlangıç zamanlarını geliştirir. Yüksek oranda yüzdesi ve derleme güncelleştirmelerinin sıklığı olan uygulamalar bu değişiklikten daha fazla avantaj sağlayabilir. Bu durumda, .NET Framework önceki sürümlerinin davranışını geri yüklemek için bu öğeyi kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, .NET Framework 4 ' te gölge kopyalamanın varsayılan başlatma davranışının nasıl devre dışı bırakılacağını ve .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyi gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Gölge Kopyalama Bütünleştirilmiş Kodları](../../../app-domains/shadow-copy-assemblies.md)
