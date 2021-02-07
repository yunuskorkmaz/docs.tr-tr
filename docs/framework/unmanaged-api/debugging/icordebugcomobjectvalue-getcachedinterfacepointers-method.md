---
description: ': ICorDebugComObjectValue:: Getcachedınterfaceişaretçiler yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 737d71f6aa903a3dfa97f583b47a322ec074147f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710861"
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
 'ndaki Yöntemin yalnızca `IInspectable` , çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınan Windows çalışma zamanı arabirimleri (arabirimler) veya tüm com arabirimlerini döndürmeyeceğini belirten bir değer.  
  
 `celt`  
 'ndaki Adresleri alınacak olan nesne sayısı.  
  
 `pceltFetched`  
 dışı `CORDB_ADDRESS` Aslında ' de döndürülen değer sayısına yönelik bir işaretçi `ptrs` .  
  
 `ptrs`  
 Önbelleğe alınmış arabirim nesnelerinin adreslerini içeren bir değer dizisinin başlangıç adresine yönelik bir işaretçi `CORDB_ADDRESS` .  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugComObjectValue Arabirimi](icordebugcomobjectvalue-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
