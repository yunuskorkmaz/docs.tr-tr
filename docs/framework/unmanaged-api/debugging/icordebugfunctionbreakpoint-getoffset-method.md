---
title: ICorDebugFunctionBreakpoint::GetOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
ms.openlocfilehash: e0e4bfb3f7adb0242456dfc3a4703ca56f118476
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138165"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a>ICorDebugFunctionBreakpoint::GetOffset Yöntemi
İşlev içindeki kesme noktasının konumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnOffset`  
 dışı Kesme noktasının uzaklığa yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
