---
title: "ICorDebugMutableDataTarget::SetThreadContext yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 077dfacc62c5bb450bc656c8fc102245d581eccc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext yöntemi
Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwThreadID`  
 [in] İşletim sistemi tarafından tanımlanan iş parçacığı tanımlayıcısı.  
  
 `contextSize`  
 [in] Boyutunu `pContext` yazılacak arabellek.  
  
 `pContext`  
 [in] Yazılacak bayt sayısı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetThreadContext` Yöntemi güncelleştirmeleri işletim sistemi tarafından tanımlanan tarafından belirtilen iş parçacığı için geçerli bağlam `dwThreadID` bağımsız değişkeni. İçerik kaydı biçimi tarafından belirtilen platform tarafından belirlenen [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi. Windows üzerinde bu olan bir [BAĞLAMI](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMutableDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
