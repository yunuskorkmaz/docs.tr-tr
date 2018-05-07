---
title: ICorDebugArrayValue::GetElement Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 500e01955666c7a8e2bd1dcf9d34afe3aeb6b421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement Metodu
Verilen dizi öğenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cdim`  
 [in] Bu boyut sayısını `ICorDebugArrayValue` nesnesi.  
  
 Bu değer ayrıca boyutudur `indices` boyutuna boyutlarını sayıya eşit olduğundan dizi `ICorDebugArrayValue` nesnesi.  
  
 `indices`  
 [in] Bir dizi dizini değerleri, her biri bir boyut içindeki konumu belirtir `ICorDebugArrayValue` nesnesi.  
  
 Bu değer null olmamalıdır.  
  
 `ppValue`  
 [out] Bir işaretçi adresine Icordebugvalue nesnenin belirtilen öğenin değerini temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
