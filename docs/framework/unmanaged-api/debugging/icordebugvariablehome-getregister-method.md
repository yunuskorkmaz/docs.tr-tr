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
ms.openlocfilehash: 7f912f4b13620b567f5aa097604e98112d85f02d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711760"
---
# <a name="icordebugvariablehomegetregister-method"></a>Icordebugvariablehome:: GetRegister yöntemi

Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRegister`  
 dışı Konum türü olan bir değişken için kaydolmayı belirten CorDebugRegister numaralandırma değeri `VLT_REGISTER` ve konum türü olan bir değişken için temel kayıt `VLT_REGISTER_RELATIVE` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntemi aşağıdaki değerleri döndürür:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Değişken, bağımsız değişkeni tarafından belirtilen kasada bulunur `pRegister` .|  
|`E_FAIL`|Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [VariableLocationType Sabit Listesi](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
