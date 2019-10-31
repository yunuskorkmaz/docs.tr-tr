---
title: 'Icordebugvariablehome:: GetRegister yöntemi'
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
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125069"
---
# <a name="icordebugvariablehomegetregister-method"></a>Icordebugvariablehome:: GetRegister yöntemi
`VLT_REGISTER`konum türüne sahip bir değişken içeren kaydı alır ve `VLT_REGISTER_RELATIVE`konum türü olan bir değişken için temel kayıt olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pRegister`  
 dışı Bir CorDebugRegister numaralandırma değeri, konum türü `VLT_REGISTER`olan bir değişken için kaydolmayı ve `VLT_REGISTER_RELATIVE`konum türü olan bir değişken için temel kayıt olduğunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Değişken `pRegister` bağımsız değişkeni tarafından belirtilen yazmaç içinde.|  
|`E_FAIL`|Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [VariableLocationType Sabit Listesi](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [ICorDebugVariableHome Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
