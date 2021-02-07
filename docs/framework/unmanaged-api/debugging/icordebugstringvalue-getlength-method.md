---
description: ': ICorDebugStringValue:: GetLength yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugStringValue::GetLength Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: ae4d42b5b65e5f80e884415a5acfc7f894ffe11e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717387"
---
# <a name="icordebugstringvaluegetlength-method"></a>ICorDebugStringValue::GetLength Yöntemi

Bu ICorDebugStringValue tarafından başvurulan dizedeki karakter sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pcchString`  
 dışı Bu nesnenin başvurduğu dizenin uzunluğunu belirten bir değer işaretçisi `ICorDebugStringValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
