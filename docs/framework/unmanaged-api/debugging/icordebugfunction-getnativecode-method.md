---
title: ICorDebugFunction::GetNativeCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb85c4b2c26c136a5f9fc05221a42c4bc99f37f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988708"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode Yöntemi
Bu ICorDebugFunction örneği tarafından temsil edilen işlev için yerel kodu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bu işlev, yalnızca derlenmiş zamanında (JIT) ayarlanmadı Microsoft Ara dili (MSIL) kodu ise bu işlev ya da null, yerel kodunu temsil eden Icordebugcode örneğine bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa bu tarafından temsil edilen işlevi `ICorDebugFunction` örneği JIT olarak derlenmiş birden çok kez, genel türler gibi söz konusu olduğunda `GetNativeCode` bir rastgele yerel kod nesnesi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
