---
title: ICorDebugRegisterSet::GetRegistersAvailable Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: 9d8bd6ab13fa408fd7390aaeb76baee274742f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137697"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable Yöntemi
Bu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) içindeki yazmaçların Şu anda kullanılabildiğini belirten bir bit maskesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAvailable`  
 dışı Şu anda hangi yazmaçların kullanılabilir olduğunu gösteren bir bit maskesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Verilen durum için değeri belirlenemiyorsa, kayıt kullanılamaz.  
  
 Döndürülen maske her kayıt için bir bit içerir (1 <, YAZMAÇ dizinini <). Kayıt kullanılabiliyorsa bit değeri 1, veya kullanılamıyorsa 0 olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
