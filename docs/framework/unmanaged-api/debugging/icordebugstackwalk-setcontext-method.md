---
description: ': Icordebugstackizlenecek yol:: SetContext yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 20e18460d237a63e4c2695b9e7cbfa766ed3908f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794721"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext Yöntemi

[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `flag`  
 'ndaki Bir [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) bayrağı, bağlamın yığındaki etkin kareden mi yoksa yığının geriye doğru bir şekilde mi devraldığını gösterir.  
  
 `contextSize`  
 'ndaki Arabelleğin ayrılan boyutu `CONTEXT` .  
  
 `context`  
 'ndaki `CONTEXT` Arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`Nesnenin bağlamı başarıyla ayarlandı.|  
|E_FAIL|`ICorDebugStackWalk`Nesnenin bağlamı ayarlanmadı.|  
|E_INVALIDARG|Bağlam null.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|Bağlam arabelleği çok küçük.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, iş parçacığının geçerli bağlamını değiştirmez.  
  
 Geçerli içeriğin geçersiz bir bağlam olarak ayarlanması, yığın denetçisi 'nden öngörülemeyen sonuçlara neden olabilir.  
  
 [Icordebugstackizlenecek yol:: GetContext](icordebugstackwalk-getcontext-method.md) yöntemini hemen çağırarak, bu bağlamın tam bit düzeyinde bir kopyasını alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
