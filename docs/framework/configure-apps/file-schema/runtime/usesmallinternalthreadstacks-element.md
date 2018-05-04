---
title: '&lt;Usesmallınternalthreadstacks&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a11b9a008878e716e9b3d8cd54abe5eb4169672a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;Usesmallınternalthreadstacks&gt; öğesi
Ortak dil çalışma zamanı (CLR) bellek miktarını azaltmak istekleri dahili olarak, bu iş parçacığı için varsayılan yığın boyutunu kullanmak yerine kullanır belirli iş parçacıklarını oluşturduğunda açık yığın boyutları belirterek kullanır.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<Usesmallınternalthreadstacks > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> Dahili olarak kullanan belirli iş parçacıklarını oluşturduğunda, istenip istenmeyeceğini CLR kullanım açık yığın boyutları yerine varsayılan yığın boyutunu belirtir. Açık yığın boyutu 1 MB varsayılan yığın boyutundan daha küçük.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Açık yığın boyutları isteyin.|  
|false|Varsayılan yığın boyutunu kullanın. Bunun için varsayılan değer [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İstek dikkate alınır, iç iş parçacığı için CLR kullanan açık iş parçacığı boyutları varsayılan boyuttan daha küçük olduğu için bu yapılandırma öğesi bir işlemde daha az sanal bellek kullanımını istemek için kullanılır.  
  
> [!IMPORTANT]
>  Bu yapılandırma öğesi mutlak bir gereksinim yerine CLR isteğidir. İçinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], istek yalnızca x86 için dikkate alınır mimarisi. Bu öğe CLR gelecek sürümlerinde tamamen göz ardı veya seçili iç iş parçacıkları için kullanılan her zaman açık yığın boyutları olarak değiştirilir.  
  
 CLR isteği geliştirir, daha küçük yığın boyutları olası yığın olun çünkü bu yapılandırma öğesi daha küçük sanal bellek kullanımı için güvenilirlik trades belirterek daha büyük bir olasılıkla taşar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, CLR kullanım açık yığın belirli dahili olarak kullandığı iş parçacıklarının boyutları isteği gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
