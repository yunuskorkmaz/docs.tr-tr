---
description: 'Hakkında daha fazla bilgi edinin: <System. Runtime. Caching> öğesi (önbellek ayarları)'
title: <system.runtime.caching> Öğesi (Önbellek Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 602d863caedef5c1334948b25b0caa2b0e35f685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652737"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.caching> Öğesi (Önbellek Ayarları)

<xref:System.Runtime.Caching.ObjectCache>Yapılandırma dosyasındaki giriş aracılığıyla varsayılan bellek içi uygulama için yapılandırma sağlar `memoryCache` .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler

`None`  

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar

Bu ad alanındaki sınıflar, ASP.NET ' deki, ancak derlemeye bağımlılık olmadan önbelleğe alma olanaklarını kullanmanın bir yolunu sunar `System.Web` . Daha fazla bilgi için bkz. [.NET Framework uygulamalarında önbelleğe alma](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Çıktı önbelleği işlevselliği ve <xref:System.Runtime.Caching> ad alanındaki türler .NET Framework 4 ' te yenidir.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, sınıfına dayalı bir önbelleğin nasıl yapılandırılacağını gösterir <xref:System.Runtime.Caching.MemoryCache> . Örnek, `namedCaches` bellek önbelleği için girdinin bir örneğinin nasıl yapılandırılacağını gösterir. Önbellek adı `name` özniteliği "varsayılan" olarak ayarlanarak varsayılan önbellek girişi adına ayarlanır.  
  
`cacheMemoryLimitMegabytes`Özniteliği ve `physicalMemoryPercentage` özniteliği sıfır olarak ayarlanır. Bu özniteliklerin sıfıra ayarlanması, <xref:System.Runtime.Caching.MemoryCache> otomatik boyutlandırma buluşsal yöntemleri varsayılan olarak kullanıldığı anlamına gelir. Önbellek uygulamasının her iki dakikada bir, geçerli bellek yükünü mutlak ve yüzde tabanlı bellek sınırlarına göre karşılaştırması gerekir.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<memoryCache> Öğesi (önbellek ayarları)](memorycache-element-cache-settings.md)
