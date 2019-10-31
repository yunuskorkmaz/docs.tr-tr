---
title: ICorDebugStackWalk::GetFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131834"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame Metodu
[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesinde geçerli kareyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFrame`  
 'ndaki Oluşturulan çerçeve nesnesinin, yığındaki geçerli çerçeveyi temsil eden adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Çalışma zamanı geçerli çerçeveyi başarıyla döndürdü.|  
|E_FAıL|Geçerli çerçeve döndürülmedi.|  
|S_FALSE|Geçerli çerçeve bir yerel yığın çerçevesidir.|  
|E_INVALIDARG|`pFrame` null.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStackWalk` yalnızca gerçek yığın çerçevelerini döndürür. İç çerçeveler döndürmek için [ICorDebugThread3:: GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın. (İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStackWalk Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
