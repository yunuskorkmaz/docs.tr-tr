---
title: ICorDebugRegisterSet2::GetRegistersAvailable Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e2e3862f91fc68879e2f9e396ab9045c617de82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable Metodu
Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `numChunks`  
 [in] Boyutunu `availableRegChunks` dizi.  
  
 `availableRegChunks`  
 [out] Bir bayt dizisi, bir kasaya her biti karşılık gelir. Bir kayıt varsa, kasanın karşılık gelen bit ayarlanır.  
  
## <a name="remarks"></a>Açıklamalar  
 CorDebugRegister numaralandırması değerlerini farklı mikro yazmaçlar belirtin. Üst beş her değerin dizine bittir `availableRegChunks` bayt dizisi. Her bir değerin alt üç BITS dizinli bayt bit konumlarını tanımlar. Verilen bir `CorDebugRegister` maske kasanın konumda belirli bir kayıt belirten değeri şu şekilde belirlenir:  
  
1.  Doğru bayt erişmesi gereken dizin ayıklamak `availableRegChunks` dizi:  
  
     `CorDebugRegister`Değer >> 3  
  
2.  Bit sıfır en az önemli bit olduğu dizinli bayt bit konumlarını ayıklayın:  
  
     `CorDebugRegister`Değer & 7  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
