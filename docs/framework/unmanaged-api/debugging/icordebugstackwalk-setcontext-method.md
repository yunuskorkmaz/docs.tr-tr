---
title: ICorDebugStackWalk::SetContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131805"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext Yöntemi
[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesinin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flag`  
 'ndaki Bir [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) bayrağı, bağlamın yığındaki etkin kareden mi yoksa yığının geriye doğru bir şekilde mi devraldığını gösterir.  
  
 `contextSize`  
 'ndaki `CONTEXT` arabelleğinin ayrılan boyutu.  
  
 `context`  
 'ndaki `CONTEXT` arabelleği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` nesnenin bağlamı başarıyla ayarlandı.|  
|E_FAıL|`ICorDebugStackWalk` nesnenin bağlamı ayarlanmadı.|  
|E_INVALIDARG|Bağlam null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Bağlam arabelleği çok küçük.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, iş parçacığının geçerli bağlamını değiştirmez.  
  
 Geçerli içeriğin geçersiz bir bağlam olarak ayarlanması, yığın denetçisi 'nden öngörülemeyen sonuçlara neden olabilir.  
  
 [Icordebugstackizlenecek yol:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemini hemen çağırarak, bu bağlamın tam bit düzeyinde bir kopyasını alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
