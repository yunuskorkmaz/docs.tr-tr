---
title: ICorDebugValue::GetAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728374"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress Metodu

Bu "ICorDebugValue" nesnesinin, hata ayıklama sürecinde olan adresini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAddress`  
 dışı `CORDB_ADDRESS` Bu değer nesnesinin adresini belirten nesne işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Değer kullanılamıyorsa 0 (sıfır) döndürülür. Bu durum, değer en az kısmen Yazmaçlarda veya çöp toplayıcı tanıtıcısında () depolanıyorsa meydana gelebilir `GCHandle` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
