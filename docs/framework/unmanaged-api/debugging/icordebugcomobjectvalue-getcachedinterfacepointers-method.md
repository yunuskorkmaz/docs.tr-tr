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
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125511"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
Geçerli çalışma zamanında çağrılabilir sarmalayıcı (RCW) üzerinde önbelleğe alınmış ham arabirim işaretçilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIInspectableOnly`  
 'ndaki Yöntemin yalnızca, çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınan Windows Çalışma Zamanı arabirimlerini (`IInspectable` arabirimleri) veya tüm COM arabirimlerini döndürmeyeceğini belirten bir değer.  
  
 `celt`  
 'ndaki Adresleri alınacak olan nesne sayısı.  
  
 `pceltFetched`  
 dışı Aslında `ptrs`döndürülen `CORDB_ADDRESS` değerlerinin sayısı için bir işaretçi.  
  
 `ptrs`  
 Önbelleğe alınmış arabirim nesnelerinin adreslerini içeren `CORDB_ADDRESS` değerleri dizisinin başlangıç adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugComObjectValue Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
