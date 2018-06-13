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
ms.openlocfilehash: 9a2ea7273fec62654c168d6786d3644b184ff7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419575"
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome::GetOffset yöntemi
Uzaklık bir değişken için temel kasadan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pOffset`  
 [out] Taban kayıt uzaklığı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi, aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Bir kayıt göreli bellek konumda değişkenidir.|  
|`E_FAIL`|Değişken bir kayıt göreli bellek konumda değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
