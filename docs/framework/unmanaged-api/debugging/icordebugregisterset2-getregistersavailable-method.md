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
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131363"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable Yöntemi
Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `numChunks`  
 'ndaki `availableRegChunks` dizisinin boyutu.  
  
 `availableRegChunks`  
 dışı Her bitin bir kayda karşılık gelen bir bayt dizisi. Bir yazmaç varsa, kaydın karşılık gelen biti ayarlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 CorDebugRegister sabit listesinin değerleri, farklı mikro işlemcilerin kayıtlarını belirtir. Her bir değerin üst beş biti, `availableRegChunks` bayt dizisinin dizinidir. Her bir değerin alt üç biti, dizinlenmiş bayt içindeki bit konumunu belirler. Belirli bir kaydı belirten `CorDebugRegister` bir değer verildiğinde, maskenin içindeki kayıt konumu aşağıdaki şekilde belirlenir:  
  
1. `availableRegChunks` dizisindeki doğru bayta erişmek için gereken dizini ayıklayın:  
  
     `CorDebugRegister` değeri > > 3  
  
2. Dizin oluşturulan bayt içindeki bit konumunu ayıklayın; burada bit sıfır en az önemli bir bittir:  
  
     `CorDebugRegister` değeri & 7  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
