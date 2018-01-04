---
title: "ICorDebugProcess::ClearCurrentException Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException Yöntemi
Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Geçerli yönetilmeyen özel durumu silinecek iş parçacığı kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemi çağırmadan önce çağırın [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ne zaman bir iş parçacığı bildirdi tarafından ayıklayıcı yoksayılmalıdır yönetilmeyen bir özel durum. Bu işlem bekleyen bant içi (IB) ve bant dışı (OOB) olayları verilen iş parçacığı üzerinde temizleyin. Tüm OOB kesme noktaları ve tek adımlı özel durumları otomatik olarak temizlenir.  
  
 Kullanım [Icordebugthread2::ınterceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) geçerli müdahale yönetilen bir iş parçacığında özel durum.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
