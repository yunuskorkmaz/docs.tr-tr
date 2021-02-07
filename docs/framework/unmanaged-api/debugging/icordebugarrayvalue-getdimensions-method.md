---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbu Garrayvalue:: GetDimensions Yöntemi'
title: ICorDebugArrayValue::GetDimensions Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 007a48891a01e5779e3f9ef10cec720d6647c8f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723107"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>ICorDebugArrayValue::GetDimensions Metodu

Bu dizinin her bir boyutundaki öğelerin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cdim`  
 'ndaki Bu ıcorınumber Garrayvalue nesnesinin boyut sayısı.  
  
 Bu değer Ayrıca, `dims` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .  
  
 `dims`  
 dışı Her biri, bu nesnedeki bir boyuttaki öğelerin sayısını belirten bir tamsayılar dizisi `ICorDebugArrayValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
