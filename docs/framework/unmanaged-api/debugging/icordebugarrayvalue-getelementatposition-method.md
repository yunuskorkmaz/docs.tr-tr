---
title: ICorDebugArrayValue::GetElementAtPosition Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: a6e5ecee9a89da98a73dfb20935c5ec594d5958f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732937"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a>ICorDebugArrayValue::GetElementAtPosition Metodu

Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `nPosition`  
 'ndaki Alınacak öğenin konumu.  
  
 `ppValue`  
 dışı Öğesinin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Çok boyutlu bir dizinin düzeni, dizi düzeninin C++ stilini izler.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
