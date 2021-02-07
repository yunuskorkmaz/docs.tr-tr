---
description: ': Icordebugmutabledatatarget:: SetThreadContext yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmutabledatatarget:: SetThreadContext yöntemi'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 4674df92b72b44e19eff663c9a17dd8ca4b5a1b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722483"
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
 'ndaki `pContext` Yazılacak arabelleğin boyutu.  
  
 `pContext`  
 'ndaki Yazılacak baytların işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetThreadContext`Yöntemi, işletim sistemi tarafından tanımlanan bağımsız değişken tarafından belirtilen iş parçacığının geçerli bağlamını güncelleştirir `dwThreadID` . Bağlam kaydının biçimi [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen platforma göre belirlenir. Windows 'ta bu bir [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) yapısıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
