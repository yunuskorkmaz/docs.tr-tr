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
ms.openlocfilehash: 8d74566b71501cf21081ac894048bb1c29e0ad94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yapılandırma dosyası şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
