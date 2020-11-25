---
title: ICorDebug::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 5cdd89ebdbb5abb9b001c1489a54bfb867808c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723434"
---
# <a name="icordebuginitialize-method"></a>ICorDebug::Initialize Yöntemi

Nesnesini başlatır `ICorDebug` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, `Initialize` hata ayıklama hizmetlerini başlatmak için oluşturma zamanında çağrılmalıdır. Bu yöntem, üzerinde başka herhangi bir yöntem çağrılmadan önce çağrılmalıdır `ICorDebug` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
