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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790984"
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

- [VariableLocationType Sabit Listesi](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
