---
title: ICorDebugType2::GetTypeID yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 463838681ceaaeb2edab85a22dd979fb143b9248
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602890"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID yöntemi
Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 [out] Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu Icordebugtype için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu. `HRESULT` Kodları şunlardır:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Yöntem, geçerli bir almıştır [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Türü yüklü değil.|  
|`CORDBG_E_UNSUPPORTED`|Türü desteklenmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, çalışma zamanına kadar yüklenmiş olabilir değil veya bir türü temsil eden Icordebugtype bir eşleme sağlar. bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), bir opak gören işleyecek yüklenen çalışma zamanına tür tanımlar.  
  
 Ne zaman Icordebugtype temsil eden tür sahip değildir ancak yüklenen, bu yöntemi döndürür `CORDBG_E_CLASS_NOT_LOADED`.  Türü desteklenmiyor varsa, döndürür `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugType2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
