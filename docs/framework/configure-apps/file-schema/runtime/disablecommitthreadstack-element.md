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
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198996"
---
# <a name="disablecommitthreadstack-element"></a>\<disableCommitThreadStack> Öğesi

Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Gerekli öznitelik.<br /><br /> Tüm iş parçacığı yığınının iş parçacığı başlangıcında (varsayılan davranış) devre dışı bırakılıp bırakılmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakmayın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.|  
|1|Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanının varsayılan davranışı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmeniz olur. Sınırlı belleği olan bir sunucuda çok sayıda iş parçacığı oluşturulması gerekiyorsa ve bu iş parçacıklarının çoğu çok az yığın alanı kullanıyorsa, ortak dil çalışma zamanı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını hemen yürütmezse sunucu daha iyi çalışabilir.  
  
> [!NOTE]
> Yönetilmeyen konaklar, `STARTUP_DISABLE_COMMITTHREADSTACK` [startup_flags](../../../unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırmasında başlangıç bayrağını kullanarak aynı sonucu elde edebilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, ortak dil çalışma zamanının varsayılan davranışının devre dışı bırakılacağını gösterir. Bu, iş parçacığı başlangıcında tam iş parçacığı yığınını yürütmek için kullanılır.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
