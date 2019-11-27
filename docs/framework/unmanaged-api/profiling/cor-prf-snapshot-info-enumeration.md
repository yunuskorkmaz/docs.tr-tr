---
title: COR_PRF_SNAPSHOT_INFO Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427276"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO Numaralandırması
Profil oluşturucunun [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Üyeleri  
  
|Üyeleri|Açıklama|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|`context` parametresi dışında tüm `StackSnapshotCallback` parametreleri için değerlerin geçirilmesi gerektiğini gösterir.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|`context` parametresi dahil olmak üzere tüm `StackSnapshotCallback` parametreleri için değerlerin geçirilmesi gerektiğini gösterir.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Daha basit, alternatif bir yığın yürüme algoritmasının kullanılacağını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_SNAPSHOT_INFO` numaralandırması tarafından verilen değerler, [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoduna parametre olarak geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
