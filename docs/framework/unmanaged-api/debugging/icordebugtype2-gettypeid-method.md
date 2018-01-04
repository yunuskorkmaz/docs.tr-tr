---
title: "ICorDebugType2::GetTypeID yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d18aa8210ea90736c0757e2587aab4ff143dcdad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu. `HRESULT` Kodları aşağıdakileri içerir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Yöntemin geçerli bir aldığı [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Türü yüklü değil.|  
|`CORDBG_E_UNSUPPORTED`|Türü desteklenmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, çalışma zamanına kadar yüklenmedi veya bir türü temsil eden Icordebugtype bir eşleme sağlar bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), bir opak gören işleyen çalışma zamanına yüklenen bir türü tanımlar.  
  
 Ne zaman Icordebugtype temsil eden tür henüz henüz yüklenirken, bu yöntem `CORDBG_E_CLASS_NOT_LOADED`.  Türü varsa desteklenmiyor, döndürür `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugType2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
