---
title: ICorDebugThread::GetActiveChain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 99a617ef21ee3c3319b1ebe7d3ab8367659b6ef8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133551"
---
# <a name="icordebugthreadgetactivechain-method"></a>ICorDebugThread::GetActiveChain Yöntemi
Bu ICorDebugThread nesnesindeki etkin (en son) yığın zincirine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppChain`  
 dışı Yığın zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Şu anda etkin bir yığın zinciri yoksa `ppChain` parametresi null.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
