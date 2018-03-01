---
title: ICorDebugCode::GetILToNativeMapping Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4477ff22d08d5f7ef291c27c00b8985f89ebebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping Metodu
Eşlemeleri Ara dili (MSIL) kaydırır Microsoft'tan yerel uzaklıkları temsil "Cor_debug_ıl_to_natıve_map" örnekleri dizisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cMap`  
 [in] Boyutunu `map` dizi.  
  
 `pcMap`  
 [out] Döndürülen öğe gerçek sayısını gösteren bir işaretçi `map` dizi.  
  
 `map`  
 [out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, her biri bir yerel uzaklığı MSIL uzaklığı bir eşleme temsil eder.  
  
 Döndürülen öğeleri dizisi sıralamaya yoktur.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetILToNativeMapping` Yöntemi yalnızca bu "ICorDebugCode" örneğinin yalnızca MSIL koddan derlenmiş zamanında (JIT) olan yerel kod temsil ediyorsa anlamlı sonuçlar döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugCode Arabirimi1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
