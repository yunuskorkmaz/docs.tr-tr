---
title: ICorDebugVariableHome::GetRegister yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 290647f0e0dcaeae53362762ed7f8e0c2f05a82c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189956"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome::GetRegister yöntemi
Konum türünde bir değişken içeren bir kayıt alır `VLT_REGISTER`hem de konum türünde bir değişken için temel kaydı `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pRegister`  
 [out] Konum türünde bir değişken için kayıt gösteren bir CorDebugRegister sabit listesi değeri `VLT_REGISTER`hem de konum türünde bir değişken için temel kaydı `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Değişkeni tarafından belirtilen kayıt defterinde olduğu `pRegister` bağımsız değişken.|  
|`E_FAIL`|Değişken, bir kayıt veya bir kayıt göreli konumu değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
