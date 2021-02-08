---
description: ': ICorDebug:: Initialize yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791601"
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
