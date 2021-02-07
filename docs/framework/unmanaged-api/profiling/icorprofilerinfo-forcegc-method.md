---
description: ': ICorProfilerInfo:: ForceGC yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1abed09450b72730a11a168223b6da05e9baf9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737551"
---
# <a name="icorprofilerinfoforcegc-method"></a>ICorProfilerInfo::ForceGC Yöntemi

Çöp toplamayı ortak dil çalışma zamanı (CLR) içinde gerçekleşmeye zorlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `ForceGC`Yöntemi yalnızca yönetilen kodu çalıştırmayan bir iş parçacığından çağrılmalıdır ve yığınında hiçbir profil oluşturucu geri çağırmaları yok. En uygun uygulama, zaman Oluşturucu içinde, sinyal edildiğinde çağıran ayrı bir iş parçacığı oluşturmaktır `ForceGC` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
