---
description: 'Şu konuda daha fazla bilgi edinin: ıcorısegarrayvalue:: GetBaseIndicies yöntemi'
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
ms.openlocfilehash: ac38123860cc3187b7dc2398b32244387d19c5ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723128"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a>ICorDebugArrayValue::GetBaseIndicies Metodu

Dizideki her boyutun temel dizinini alır.  
  
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
 'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` . Bu değer Ayrıca, `indicies` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .  
  
 `indicies`  
 dışı Her biri, bu nesnenin bir boyutunun temel dizini (yani, başlangıç dizini) olan tamsayılar dizisi `ICorDebugArrayValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
