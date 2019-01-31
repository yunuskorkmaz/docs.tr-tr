---
title: <disableCommitThreadStack> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5071b2c23b25d6368c84582b76c1f8d18e2a3dff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257527"
---
# <a name="disablecommitthreadstack-element"></a>\<disableCommitThreadStack > öğesi
Bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının taahhüt olup olmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<disableCommitThreadStack>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> İş parçacığı başlangıç (varsayılan davranış) üzerinde tam iş parçacığı yığın Yürütülüyor etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında tam iş parçacığı yığını tamamlamaya olduğu devre dışı bırakmayın.|  
|1.|İş parçacığı yığınının tamamının bir iş parçacığı başlatıldığında işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğe ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının işleme sağlamaktır. Hemen bir iş parçacığı st olduğunda ortak dil çalışma zamanı iş parçacığı yığınının tamamının kaydetmeyen bir işlevi, sunucu çok sayıda iş parçacığı belleğin sınırlı olduğu bir sunucuda oluşturulması gerekir ve bu iş parçacıklarının en çok az yığın alanı kullanır, daha iyi gerçekleştirebilir başlatıldı.  
  
> [!NOTE]
>  Yönetilmeyen konak kullanabilir `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağı [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) aynı sonuca ulaşmak için sabit listesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iş parçacığı yığınının tamamının iş parçacığı başlangıç işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakmak gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
