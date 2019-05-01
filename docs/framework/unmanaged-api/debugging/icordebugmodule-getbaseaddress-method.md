---
title: ICorDebugModule::GetBaseAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 763f2872099fac87138b7e1ab058c60475892b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994922"
---
# <a name="icordebugmodulegetbaseaddress-method"></a>ICorDebugModule::GetBaseAddress Yöntemi
Modül temel adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAddress`  
 [out] A `CORDB_ADDRESS` modülü temel adresini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Modül bir yerel ise (diğer bir deyişle, modül NGen.exe yerel Görüntü Oluşturucu tarafından üretilmişse) görüntü, temel adresini sıfır olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
