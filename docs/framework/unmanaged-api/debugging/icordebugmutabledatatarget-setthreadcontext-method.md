---
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132703"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>Icordebugmutabledatatarget:: SetThreadContext yöntemi
Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwThreadID`  
 'ndaki İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.  
  
 `contextSize`  
 'ndaki Yazılacak `pContext` arabelleğinin boyutu.  
  
 `pContext`  
 'ndaki Yazılacak baytların işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetThreadContext` yöntemi, işletim sistemi tarafından tanımlanan `dwThreadID` bağımsız değişkeni tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir. Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir. Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
