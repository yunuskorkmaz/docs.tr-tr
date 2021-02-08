---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugAssemblyEnum:: Next yöntemi'
title: ICorDebugAssemblyEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: feb77f22ec59fcc0e1b3f5590b7aee4efba13d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772230"
---
# <a name="icordebugassemblyenumnext-method"></a>ICorDebugAssemblyEnum::Next Yöntemi

Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda derlemeyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki Alınacak derleme sayısı.  
  
 `values`  
 dışı Her biri bir derlemeyi temsil eden ICorDebugAssembly nesnesine işaret eden işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Aslında döndürülen derleme sayısına yönelik bir işaretçi. Bu değer bir ise null olabilir `celt` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
