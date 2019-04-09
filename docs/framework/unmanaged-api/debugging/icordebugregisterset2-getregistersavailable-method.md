---
title: ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ee807ae17e4d53d3f6f3963f5a91df0a2dddd0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099878"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi
Bir bit eşlem kullanılabilir kayıtlara sağlayan bayt dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `numChunks`  
 [in] Boyutu `availableRegChunks` dizisi.  
  
 `availableRegChunks`  
 [out] Bir bayt dizisi, bir kasaya her bitini karşılık gelir. Bir kayıt varsa, kasanın karşılık gelen bit ayarlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 CorDebugRegister sabit listesi değerlerini farklı mikro kasalar belirtin. Her bir değerin üst beş biti dizine olan `availableRegChunks` bayt dizisi. Her bir değerin alt üç bit dizinli bayt içindeki bit konumu belirleyin. Verilen bir `CorDebugRegister` belirli bir kaydı, maske kasanın konumu belirten bir değer şu şekilde belirlenir:  
  
1.  Doğru bayt erişmesi gereken dizin ayıklamak `availableRegChunks` dizisi:  
  
     `CorDebugRegister` Değer >> 3  
  
2.  Bit sıfır en az önemli bite olduğu dizinli bayt içindeki bit konumu ayıklayın:  
  
     `CorDebugRegister` Değer & 7  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
