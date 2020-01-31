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
ms.openlocfilehash: b76d17337408653d130ee0cb8594e759bdade37c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791863"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next Yöntemi
[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).|  
|E_FAIL|`ICorDebugStackWalk` nesnesi gelişmiş bir nesne olamaz.|  
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

- [ICorDebugStackWalk Arabirimi](icordebugstackwalk-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
