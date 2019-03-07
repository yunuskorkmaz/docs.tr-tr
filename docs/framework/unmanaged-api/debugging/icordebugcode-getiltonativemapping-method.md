---
title: ICorDebugCode::GetILToNativeMapping Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2ae79e53d6f87dca24dff105b9538e04b667fd1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485945"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping Metodu
Eşlemeleri için yerel uzaklıklar Microsoft Ara dili (MSIL) kaydırır temsil eden "Cor_debug_ıl_to_natıve_map" örneklerinin bir dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cMap`  
 [in] Boyutu `map` dizisi.  
  
 `pcMap`  
 [out] Gerçek döndürülen öğe sayısına bir işaretçi `map` dizisi.  
  
 `map`  
 [out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları, her biri bir MSIL uzaklık bir eşleme yerel uzaklık temsil eder.  
  
 Sıralama yok döndürülen öğe dizisi yok.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping` Yöntemi yalnızca bu "ICorDebugCode" örneği, yalnızca derlenmiş MSIL kodunu zamanında (JIT) yerel kod temsil ediyorsa anlamlı sonuçlar döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Icordebugcode arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
