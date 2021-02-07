---
description: ': ICorDebugCode:: GetILToNativeMapping Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 808ed450fced8afecc2b637a3b990a894897b350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711199"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping Metodu

Microsoft ara dili (MSIL) uzaklıklarından yerel uzaklıklara olan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cMap`  
 'ndaki `map` Dizinin boyutu.  
  
 `pcMap`  
 dışı Dizide döndürülen gerçek öğe sayısı için bir işaretçi `map` .  
  
 `map`  
 dışı `COR_DEBUG_IL_TO_NATIVE_MAP` Her biri BIR MSIL öğesinden yerel bir uzaklığa bir eşlemeyi temsil eden yapıların dizisi.  
  
 Döndürülen öğelerin dizisinde bir sıralama yoktur.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetILToNativeMapping`Yöntemi, yalnızca bu "ICorDebugCode" örneği, MSIL kodundan derlenen yerel kodu (JIT) gösterirse anlamlı sonuçlar döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode Arabirimi](icordebugcode-interface1.md)
