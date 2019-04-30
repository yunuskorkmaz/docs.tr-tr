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
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645376"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame Metodu
Etkin alır (yani, en son) zincirindeki çerçeve.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
