---
title: "&lt;Thread_UseAllCpuGroups&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c574d6f5598616776e891ab282c703ce20bc6960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; öğesi
Çalışma zamanı, tüm CPU gruplarında yönetilen iş parçacığı dağıtır olup olmadığını belirtir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanı, tüm CPU gruplarında yönetilen iş parçacığı dağıtır olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Çalışma zamanı yönetilen iş parçacığı birden çok CPU gruplarında dağıtmaz. Bu varsayılandır.|  
|`true`|Bilgisayarda birden çok CPU grupları varsa çalışma zamanı yönetilen iş parçacığı birden çok CPU grubu içinde dağıtır ve [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi etkindir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğe etkinleştirme yönetilen iş parçacığı tüm CPU gruplarında dağıtmak çalışma zamanı neden olur. Bu özelliği kullanmak için da etkinleştirmeniz gerekir [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi, tüm CPU gruplarına çöp toplama genişleten ve tüm çekirdek oluştururken ve yığın Dengeleme dikkate alır. Etkinleştirme [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) öğesi gerektiriyor etkinleştirme [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) öğesi. Bu öğeleri etkinleştirilmezse, etkinleştirme `<Thread_UseAllCpuGroups>` öğesi etkisi yoktur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birden çok CPU grupları desteğini etkinleştirmek gösterilmiştir.  
  
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
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<GCCpuGroup > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
