---
title: "&lt;disableCommitThreadStack&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7961c62d46a10767b119c4c55a4b620e1ad782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disableCommitThreadStack&gt; öğesi
Bir iş parçacığı başlatıldığında tam iş parçacığı yığın kaydedilmiş olup olmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<disableCommitThreadStack >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> İş parçacığı başlangıç (varsayılan davranış) tam iş parçacığı yığında yürüten devre dışı olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Ortak dil çalışma zamanı varsayılan davranışının bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya olduğu devre dışı bırakmayın.|  
|1.|Ortak dil çalışma zamanı varsayılan davranışının bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya olduğu devre dışı bırakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesinde ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya ' dir. Hemen bir iş parçacığı st olduğunda ortak dil çalışma zamanı tam iş parçacığı yığın yürütme değil, sunucunun çok sayıda iş parçacığı bellek sınırlı bir sunucuda oluşturulması gerekir ve bu iş parçacıklarının en çok az yığın alanı kullanır, daha iyi gerçekleştirebilir arted.  
  
> [!NOTE]
>  Yönetilmeyen konakları kullanabileceğiniz `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağı [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) aynı sonucu gerçekleştirmek için numaralandırması.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iş parçacığı başlangıç tam iş parçacığı yığında tamamlamaya olduğu ortak dil çalışma zamanı varsayılan davranışı devre dışı bırakma gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
