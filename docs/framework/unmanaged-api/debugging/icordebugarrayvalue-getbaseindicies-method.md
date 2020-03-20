---
title: ICorDebugArrayValue::GetBaseIndicies Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: 7c6d1905cdbd12b960014e687034ea9d163b68d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179033"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a>ICorDebugArrayValue::GetBaseIndicies Metodu
Dizideki her boyutun temel dizisini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cdim`  
 [içinde] Bu `ICorDebugArrayValue` nesnenin boyutlarının sayısı. Boyutu `indicies` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan, bu değer de dizinin boyutudur.  
  
 `indicies`  
 [çıkış] Her biri bu `ICorDebugArrayValue` nesnenin bir boyutunun temel dizini (yani başlangıç dizini) olan bir tamsayı dizisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
