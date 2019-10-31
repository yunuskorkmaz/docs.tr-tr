---
title: ICorDebugStackWalk::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 8cebb66ecf298eaaca0e7af23a9b8c6a2932c23f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131823"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next Yöntemi
[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).|  
|E_FAıL|`ICorDebugStackWalk` nesnesi gelişmiş bir nesne olamaz.|  
|CORDBG_S_AT_END_OF_STACK|Bu geriye doğru bir sonuç olarak yığının sonuna ulaşıldı.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `Next` yöntemi, `ICorDebugStackWalk` nesnesini çağıran çerçeveye ilerletir ve yalnızca çalışma zamanı geçerli çerçeveyi geriye doğru geri alabilir. Aksi halde, nesne, çalışma zamanının geriye doğru geri yükleyebilmesini sağlayan bir sonraki çerçeveye ilerler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStackWalk Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
