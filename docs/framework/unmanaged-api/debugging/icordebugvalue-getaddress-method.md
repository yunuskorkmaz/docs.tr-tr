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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac550ee7b1d66612557b30d15c275c90cf09b8af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187362"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress Metodu
Ayıklanan sürecinde olan "ICorDebugValue" nesnenin adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAddress`  
 [out] İşaretçi bir `CORDB_ADDRESS` bu değeri nesnenin adresini belirten bir nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Değer kullanılamıyor, 0 (sıfır) döndürülür. Bu değer, en azından kısmen kayıtlara ise meydana gelmiş olabilir ya da bir çöp toplayıcı tanıtıcısı depolanan (`GCHandle`).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
