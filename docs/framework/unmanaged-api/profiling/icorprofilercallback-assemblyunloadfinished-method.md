---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d757a0455992bc82ead922a5fbf4c71f11a9085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450875"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
Profil Oluşturucu bütünleştirilmiş kaldırıldı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `assemblyId`  
 [in] Boşaltılıyor derlemeyi tanımlar.  
  
 `hrStatus`  
 [in] Derleme başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.  
  
## <a name="remarks"></a>Açıklamalar  
 Değeri `assemblyId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) yöntemi döndürür.  
  
 Derleme kaldırılması, bazı bölümleri sonra devam edebilir `AssemblyUnloadFinished` geri çağırma. HRESULT hata içinde `hrStatus` hata gösterir. Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca derleme kaldırılması ilk parçası başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
