---
title: 'Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: abaf2d0542e16f526ecbe369370c31c225808f1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139344"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi
Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwThreadId`  
 İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.  
  
 `continueStatus`  
 İstenen yeni Devamlılık durumunu temsil eden bir [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı, geçerli hata ayıklama olayının normalde işlenme yönteminden farklı bir şekilde işlenmesini gerektiren bir ICorDebug yöntemi çağırdığında `ContinueStatusChanged` yöntemini çağırır. Örneğin, bekleyen bir özel durum varsa ve hata ayıklayıcı özel durumu iptal eden bir işlem isterse ( [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) veya `FuncEval`), bu API, özel durumun iptal edilmesini istemek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
