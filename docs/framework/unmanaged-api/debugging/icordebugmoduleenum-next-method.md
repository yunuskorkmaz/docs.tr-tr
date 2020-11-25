---
title: ICorDebugModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: a4bdac42c584d5d34b072354de65ed20c6a80609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709498"
---
# <a name="icordebugmoduleenumnext-method"></a>ICorDebugModuleEnum::Next Yöntemi

`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugModule" örneklerinin sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki `ICorDebugModule` Alınacak örnek sayısı.  
  
 `modules`  
 dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugModule` .  
  
 `pceltFetched`  
 dışı `ICorDebugModule` Aslında döndürülen örnek sayısına yönelik işaretçi. Bu değer bir ise null olabilir `celt` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
