---
title: ICorDebugVariableHome::GetOffset yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864cb893511bceabd61ce0064065b3866ce01dfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986758"
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome::GetOffset yöntemi
Uzaklık, bir değişken için temel kasadan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pOffset`  
 [out] Temel kayıt uzaklığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Register-göreli bellek konumunda değişkendir.|  
|`E_FAIL`|Değişken bir kayıt göreli bellek konumda değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
