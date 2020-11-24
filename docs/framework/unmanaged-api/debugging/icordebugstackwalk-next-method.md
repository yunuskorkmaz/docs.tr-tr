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
ms.openlocfilehash: 497dda473e6510cfa31405b2066c63b1a70dd5e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677329"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next Yöntemi

[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).|  
|E_FAIL|`ICorDebugStackWalk`Nesne gelişmiş olamaz.|  
|CORDBG_S_AT_END_OF_STACK|Bu geriye doğru bir sonuç olarak yığının sonuna ulaşıldı.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 `Next`Yöntemi, `ICorDebugStackWalk` yalnızca çalışma zamanı geçerli çerçeveyi geriye doğru bir şekilde geri alıyorsa nesneyi çağıran çerçeveye ilerletir. Aksi halde, nesne, çalışma zamanının geriye doğru geri yükleyebilmesini sağlayan bir sonraki çerçeveye ilerler.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStackWalk Arabirimi](icordebugstackwalk-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
