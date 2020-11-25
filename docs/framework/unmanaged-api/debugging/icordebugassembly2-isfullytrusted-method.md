---
title: ICorDebugAssembly2::IsFullyTrusted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: 8a2a6be0db76f5ee2c7fa67c2038e0a5c845bd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719716"
---
# <a name="icordebugassembly2isfullytrusted-method"></a>ICorDebugAssembly2::IsFullyTrusted Yöntemi

Derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verilip verilmediğini gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbFullyTrusted`  
 [out] `true` derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verildiyse; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, derleme için güvenlik ilkesi henüz çözümlenmemişse, yani derlemede hiçbir kod henüz çalıştırılmadıysa, bir HRESULT CORDBG_E_NOTREADY döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
