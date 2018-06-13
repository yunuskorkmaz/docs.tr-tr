---
title: ICorDebugHeapValue::IsValid Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413514"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid Yöntemi
Bu Icordebugheapvalue tarafından temsil edilen nesne geçerli olup olmadığını belirten bir değer alır.  
  
 Bu yöntem .NET Framework sürüm 2.0 kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbValid`  
 [out] Yığında bu değerin geçerli olup olmadığını gösteren bir Boole değeri için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çöp toplayıcı tarafından iadesi varsa değeri geçersiz.  
  
 Bu yöntem kullanım dışı bırakıldı. .NET Framework 2.0 tüm değerleri kadar geçerli [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , hangi saat değerleri geçersiz kılınan sırasında çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
