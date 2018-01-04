---
title: "ICorProfilerCallback::AssemblyUnloadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ead41718e0253de599019112178d64c0ab706924
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
