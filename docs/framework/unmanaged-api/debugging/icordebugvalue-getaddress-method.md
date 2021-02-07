---
description: ': ICorDebugValue:: GetAddress yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c922388fbab820e50edffc140be94a2c0920099d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690437"
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
 dışı `CORDB_ADDRESS` Bu değer nesnesinin adresini belirten nesne işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Değer kullanılamıyorsa 0 (sıfır) döndürülür. Bu durum, değer en az kısmen Yazmaçlarda veya çöp toplayıcı tanıtıcısında () depolanıyorsa meydana gelebilir `GCHandle` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
