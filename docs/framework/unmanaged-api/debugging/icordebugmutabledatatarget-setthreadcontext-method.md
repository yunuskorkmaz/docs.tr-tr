---
title: ICorDebugMutableDataTarget::SetThreadContext yöntemi
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8b3fd9940bd11c3d026b46247e0657c82b18099
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120009"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext yöntemi
Bir iş parçacığı bağlamı (yazmaç değerlerini) ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwThreadID`  
 [in] İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.  
  
 `contextSize`  
 [in] Boyutu `pContext` arabelleğe yazılacak.  
  
 `pContext`  
 [in] Yazılacak bayt için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetThreadContext` Yöntemi güncelleştirmeleri işletim sistemi tarafından tanımlanan tarafından belirtilen iş parçacığı için geçerli bağlam `dwThreadID` bağımsız değişken. Bağlam kaydı biçimi tarafından belirtilen platform tarafından belirlenir [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi. Windows üzerinde bu, bir [bağlam](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
