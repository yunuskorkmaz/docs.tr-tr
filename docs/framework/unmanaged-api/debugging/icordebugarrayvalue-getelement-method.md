---
title: ICorDebugArrayValue::GetElement Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179005"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement Yöntemi
Verilen dizi öğesinin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cdim`  
 [içinde] Bu `ICorDebugArrayValue` nesnenin boyutlarının sayısı.  
  
 Boyutu `indices` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan, bu değer de dizinin boyutudur.  
  
 `indices`  
 [içinde] Her biri `ICorDebugArrayValue` nesnenin bir boyutu içinde bir konum belirtir dizin değerleri dizisi.  
  
 Bu değer null olmamalıdır.  
  
 `ppValue`  
 [çıkış] Belirtilen öğenin değerini temsil eden bir ICorDebugValue nesnesinin adresine işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
