---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7998275ae1e80a87354dd5b3a8b0a1aa73b3b987
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674782"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > öğesi
Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<GCCpuGroup>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çöp toplama, birden fazla CPU grubu destekleyip desteklemediğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çöp toplama, birden fazla CPU grubu desteklemiyor. Bu varsayılandır.|  
|`true`|Sunucu çöp toplama etkin olduğunda çöp toplama, birden fazla CPU grubu destekler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ne zaman bir bilgisayarda birden fazla CPU grubu ve sunucu çöp toplama etkin (bkz [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğe), bu öğenin etkinleştirilmesi, çöp toplama, tüm CPU grupları arasında genişletir ve tüm çekirdek içine alır hesabı oluştururken ve Yığınlar Dengeleme.  
  
> [!NOTE]
>  Bu öğe yalnızca çöp toplama iş parçacığı için geçerlidir. Kullanıcı iş parçacıklarını tüm CPU grupları arasında dağıtmak çalışma zamanını etkinleştirmek üzere, ayrıca etkinleştirmelisiniz [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çöp toplama için birden fazla CPU grubu etkinleştirmek gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Eş zamanlı çöp toplama devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [İş istasyonu ve sunucu çöp toplama](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
