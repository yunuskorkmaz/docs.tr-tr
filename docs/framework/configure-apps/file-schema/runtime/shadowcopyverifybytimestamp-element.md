---
title: '&lt;shadowCopyVerifyByTimestamp&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a97c8708c7d57d1a8f5335ef19e8e74cb6487276
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610911"
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt; öğesi
Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmayacağını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını geri döner.  
  
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
|Etkin|Gerekli öznitelik.<br /><br /> Gölge kopyalama kullanan bir uygulama etki alanları önce gölge kopyalama bütünleştirilmiş kod derleme güncelleştirilip güncelleştirilmediğini belirlemek için başlatma sırasında derleme zaman damgaları karşılaştırma olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Başlangıçta, yalnızca son gölge kopya dizine kopyalanan bu yana güncelleştirilen derlemeleri kopyalar. İçin varsayılan [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|.NET Framework'ün önceki sürümlerini başlangıç davranışını, başlangıçta tüm dosyaları kopyalamak için olduğu döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], yalnızca kendi zaman damgaları gölge kopya dizine son kopyalanan olduğundan bunlar değişmiş gösteriyorsa gölge derlemelerdir. Bu bölümünde anlatıldığı gibi gölge kopyalama, kullanma, birçok uygulama için başlangıç sürelerini iyileştirir [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Yüksek yüzdesi ve derleme güncelleştirme sıklığına sahip uygulamalar, bu değişiklik davranış avantajlı olmayabilir. Bu durumda, bu öğe, .NET Framework'ün önceki sürümlerini davranışı geri yüklemek için kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gölge kopyalama varsayılan başlangıç davranışını devre dışı bırakma gösterir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve .NET Framework'ün önceki sürümlerini başlangıç davranışını geri döndür.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Gölge Kopyalama Bütünleştirilmiş Kodları](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
