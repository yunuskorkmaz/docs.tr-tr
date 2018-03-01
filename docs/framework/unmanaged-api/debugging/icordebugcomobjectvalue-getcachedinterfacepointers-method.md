---
title: ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
Geçerli çalışma zamanı aranabilir sarmalayıcısı üzerinde (RCW) önbelleğe ham arabirim işaretçileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bIInspectableOnly`  
 [in] Yöntem yalnızca döndürür olup olmadığını belirten bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı aranabilir sarmalayıcısı (RCW) önbelleğe alınan tüm COM arabirimleri.  
  
 `celt`  
 [in] Alınacak olan adresler nesnelerin sayısı.  
  
 `pceltFetched`  
 [out] Sayısını gösteren bir işaretçi `CORDB_ADDRESS` gerçekte döndürülen değerleri `ptrs`.  
  
 `ptrs`  
 Bir dizi başlangıç adresini gösteren bir işaretçi `CORDB_ADDRESS` adreslerini içeren bir değerler arabirimi nesneleri önbelleğe alınmış.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugComObjectValue Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
