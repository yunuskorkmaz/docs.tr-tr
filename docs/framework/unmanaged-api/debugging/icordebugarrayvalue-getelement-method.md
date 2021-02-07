---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgarrayvalue:: GetElement Yöntemi'
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
ms.openlocfilehash: dfae074b78735934d1e71b13ce01c24741a5f2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723068"
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
 'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` .  
  
 Bu değer Ayrıca, `indices` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .  
  
 `indices`  
 'ndaki Her biri nesnenin boyutu içinde bir konum belirten Dizin değerleri dizisi `ICorDebugArrayValue` .  
  
 Bu değer null olmamalıdır.  
  
 `ppValue`  
 dışı Belirtilen öğenin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
