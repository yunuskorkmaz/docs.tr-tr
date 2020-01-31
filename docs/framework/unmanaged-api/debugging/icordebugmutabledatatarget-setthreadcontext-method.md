---
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 063c7954543174caece6f3dcbe005a4b2d059c64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792842"
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
 `SetThreadContext` yöntemi, işletim sistemi tarafından tanımlanan `dwThreadID` bağımsız değişkeni tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir. Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir. Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
