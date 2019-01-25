---
title: ICorProfilerInfo::ForceGC Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c30a666dcbac553d05cc5f54d5dbb326eb6a10e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706702"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC Yöntemi
Ortak dil çalışma zamanı içinde (CLR) gerçekleşmesi için çöp toplama zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `ForceGC` Yönetilen kod asla çalıştırıldı ve tüm profil oluşturucu geri aramaları, yığın üzerinde yok. bir iş parçacığından metodu çağrılmalıdır. Çağıran profil oluşturucu içinde ayrı bir iş parçacığı oluşturmak için en kolay uygulamadır `ForceGC` erdiği zaman.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
