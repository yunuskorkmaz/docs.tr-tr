---
title: "ICorDebugStackWalk::SetContext Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00e278df2b23d6fddb18c24eefb3f2aa4d1cc3cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext Yöntemi
Ayarlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flag`  
 [in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) yığında etkin çerçeveden bağlam mi yoksa bir bağlam elde yığını geriye doğru izleme tarafından mı olduğunu belirten bayrak.  
  
 `contextSize`  
 [in] Ayrılmış boyutu `CONTEXT` arabellek.  
  
 `context`  
 [in] `CONTEXT` Arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` Nesnenin içerik başarıyla ayarlandı.|  
|E_FAIL|`ICorDebugStackWalk` Nesnenin bağlam ayarlanamadı.|  
|E_INVALIDARG|Bağlamı null şeklindedir.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Bağlam arabellek çok küçük.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, geçerli iş parçacığının içeriği değiştirmez.  
  
 Geçerli bağlam için geçersiz bir bağlam ayarı yığını walker öngörülemeyen sonuçlara neden olabilir.  
  
 Hemen çağırarak bu bağlamda tam bir bit düzeyinde kopyasını alabilirsiniz [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
