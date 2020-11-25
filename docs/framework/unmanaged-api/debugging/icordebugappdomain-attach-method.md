---
title: ICorDebugAppDomain::Attach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: d133cacb611a1c7bd03d7653f46c2e5fb1acc043
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723356"
---
# <a name="icordebugappdomainattach-method"></a>ICorDebugAppDomain::Attach Yöntemi

Hata ayıklayıcıyı uygulama etki alanına iliştirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, olayları almak ve uygulama etki alanında hata ayıklamayı etkinleştirmek için uygulama etki alanına iliştirilmelidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
