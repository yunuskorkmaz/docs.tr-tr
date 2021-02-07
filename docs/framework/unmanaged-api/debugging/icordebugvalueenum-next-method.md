---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugValueEnum:: Next yöntemi'
title: ICorDebugValueEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 9a02c769f69651227669eb4b3f8c5ce41b670a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690112"
---
# <a name="icordebugvalueenumnext-method"></a>ICorDebugValueEnum::Next Yöntemi

Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugValue" örneklerinin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki `ICorDebugValue` Alınacak örnek sayısı.  
  
 `values`  
 dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugValue` .  
  
 `pceltFetched`  
 dışı `ICorDebugValue` Aslında döndürülen örnek sayısına yönelik işaretçi. Bu değer bir ise null olabilir `celt` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
