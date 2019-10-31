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
ms.openlocfilehash: 906ca2540e421953b3ce39300aa7b2376f789929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137094"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress Metodu
Bu "ICorDebugValue" nesnesinin, hata ayıklama sürecinde olan adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAddress`  
 dışı Bu değer nesnesinin adresini belirten `CORDB_ADDRESS` nesnesine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değer kullanılamıyorsa 0 (sıfır) döndürülür. Bu durum, değer en az kısmen Yazmaçlarda veya bir çöp toplayıcı tanıtıcısında (`GCHandle`) depolanıyorsa meydana gelebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
