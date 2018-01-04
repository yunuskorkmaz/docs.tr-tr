---
title: "ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ba8fe9b0d4a09bdfe3d3e6459f16bf041dc396a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged yöntemi
Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwThreadId`  
 İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.  
  
 `continueStatus`  
 A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)yeni temsil eden değer istenen devamlılık durumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı çağrıları `ContinueStatusChanged` Icordebug yöntemi, çağırdığında yöntemi içinde normalde işlenecek şekilde potansiyel olarak farklı şekilde ele alınması için geçerli hata ayıklama olayı gerektirir. Örneğin, bekleyen bir istisna vardır ve özel durum iptal bir işlem hata ayıklayıcı isterse (gibi [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) veya `FuncEval`), bu API, özel durum olmasını istemek için kullanılır iptal edildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
