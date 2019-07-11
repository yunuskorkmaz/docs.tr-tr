---
title: ICorDebugVariableHome::GetSlotIndex yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 199c3ba5d5b9588db4c665070b4dec6266cefc2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760351"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome::GetSlotIndex yöntemi
Yerel değişken yönetilen yuvası dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pSlotIndex`  
 [out] Bir yerel değişken dizini yuva için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerleri döndürür.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Bir yuva dizin değeri yöntem çağrısından döndürülen `pSlotIndex`.|  
|`E_FAIL`|Geçerli [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği, işlev bağımsız değişkeni temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yuva dizin, bu yerel değişken için meta verileri almak için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
