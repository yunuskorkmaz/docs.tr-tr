---
title: ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da0e62250dbef9be93ccee7020e23c3f83e85592
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749910"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
Geçerli çalışma zamanı çağrılabilir sarmalayıcı üzerinde (RCW) önbelleğe alınan ham arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIInspectableOnly`  
 [in] Yöntemi yalnızca döndürür olup olmadığını gösteren bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) önbelleğe alınan tüm COM arabirimleri.  
  
 `celt`  
 [in] Alınacak adresleri olan nesneler sayısı.  
  
 `pceltFetched`  
 [out] Bir işaretçi sayısına `CORDB_ADDRESS` gerçekte döndürülen değerleri `ptrs`.  
  
 `ptrs`  
 Başlangıç adresi içeren bir dizinin işaretçisi `CORDB_ADDRESS` adresleri içeren değerler önbelleğe alınmış arabirim nesnelerini.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugComObjectValue Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
