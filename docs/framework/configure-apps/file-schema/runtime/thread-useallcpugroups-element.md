---
title: '&lt;Thread_UseAllCpuGroups&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a3984d594d0739d4b8f2b7b165aab434e10ab80
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611015"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; öğesi
Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
< Thread_UseAllCpuGroups >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanının yönetilen iş parçacıkları arasında birden fazla CPU grubu dağıtmaz. Bu varsayılandır.|  
|`true`|Bilgisayarda birden fazla CPU grubu varsa çalışma zamanı yönetilen iş parçacıklarını birden çok CPU grupları arasında dağıtır ve [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğe etkin.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bilgisayara birden fazla CPU grubu varsa, bu öğenin etkinleştirilmesi, çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmak neden olur. Bu özelliği kullanmak için ayrıca etkinleştirmelisiniz [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi, çöp toplama için tüm CPU grupları genişletir ve tüm çekirdek oluştururken ve Yığınlar Dengeleme dikkate alır. Etkinleştirme [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi gerektiriyor etkinleştirme [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi. Bu öğeler etkinleştirilmezse, etkinleştirme `<Thread_UseAllCpuGroups>` öğesi hiçbir etkiye sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok CPU için desteğini nasıl etkinleştireceğinizi gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [\<GCCpuGroup > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
