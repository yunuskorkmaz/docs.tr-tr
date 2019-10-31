---
title: ICorDebugChainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 3c11a0547ad5acc5613324d7e9d7439d44549dbc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125806"
---
# <a name="icordebugchainenumnext-method"></a>ICorDebugChainEnum::Next Yöntemi
Geçerli konumdan başlayarak sabit listesinden belirtilen ıcordebugzincirine örnek sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak `ICorDebugChain` örneklerinin sayısı.  
  
 `chains`  
 dışı Her biri zinciri temsil eden bir `ICorDebugChain` nesnesine işaret eden işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Gerçekten döndürülen `ICorDebugChain` örneklerinin sayısına yönelik bir işaretçi. `celt` bir tane ise bu değer null olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
