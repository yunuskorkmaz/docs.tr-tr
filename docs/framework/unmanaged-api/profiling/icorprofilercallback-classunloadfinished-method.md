---
title: ICorProfilerCallback::ClassUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebf72fe4f9fae5b3d791e6eed2e9421b9f4e3296
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450823"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>ICorProfilerCallback::ClassUnloadFinished Yöntemi
Profil Oluşturucu bir sınıf kaldırılması tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] Kaldırıldı sınıfı tanımlar.  
  
 `hrStatus`  
 [in] Sınıf başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ClassUnloadFinished` geri çağırma. HRESULT hata içinde `hrStatus` hata gösterir. Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk sınıfı kaldırılması parçası başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ClassUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
