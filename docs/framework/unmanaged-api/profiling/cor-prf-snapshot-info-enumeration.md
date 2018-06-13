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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450723"
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO Numaralandırması
Ne kadar veri geçirmek için Profil Oluşturucu'nın her çağrıda yığın anlık görüntüleri geri belirtir [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üyeler|Açıklama|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` parametreleri dışında `context` parametresi.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` dahil parametreleri `context` parametresi.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Bir daha basit, alternatif yığını taramasını algoritması kullanılacak gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından sağlanan değerler `COR_PRF_SNAPSHOT_INFO` numaralandırması için parametre olarak geçirilen [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
