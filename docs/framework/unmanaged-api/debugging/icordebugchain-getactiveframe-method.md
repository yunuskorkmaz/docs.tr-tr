---
title: ICorDebugChain::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79f3b3b976b83eb99f8aa26d38a1fe316de471a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744988"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame Metodu
Etkin alır (yani, en son) zincirindeki çerçeve.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppFrame`  
 [out] Etkin temsil eden Icordebugframe nesnenin adresini bir işaretçiye (diğer bir deyişle, en son) zincirindeki çerçeve.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen yığın çerçeve varsa `ppFrame` ayarlanır null.  
  
 Etkin çerçeveye kullanılabilir durumda değilse, çağrı başarılı olacaktır ve `ppFrame` null olacaktır. Etkin çerçeve CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirleri için ve başlatılan CHAIN_CLASS_INIT nedeniyle bazı zincirleri için kullanılabilir olmayacak. CorDebugChainReason numaralandırması bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
