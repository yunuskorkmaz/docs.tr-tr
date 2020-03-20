---
title: ICorDebugHeapEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178859"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next Yöntemi
Yönetilen yığındaki nesneler hakkında bilgi içeren belirtilen COR_HEAPOBJECT [örnek](cor-heapobject-structure.md) sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 Celt  
 [içinde] Alınacak nesne sayısı.  
  
  nesneleri  
 [çıkış] Her biri yönetilen yığındaki bir nesne hakkında bilgi sağlayan [COR_HEAPOBJECT](cor-heapobject-structure.md) nesneyi işaret eden bir dizi işaretçi.  
  
 pceltFetched  
 [çıkış] Gerçekte döndürülen [COR_HEAPOBJECT](cor-heapobject-structure.md) nesne sayısına `objects`işaretçi Bu değer `null` 1 `celt` ise olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Alan, `COR_HEAPOBJECT.type` iç içe başvuru sayılan COM arabiriminin tanımlayıcısIdır. Bu başvuru, `ICorDebugHeapEnum::Next`'' 'yi arayan kişi tarafından serbest bırakılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapEnum Arabirimi](icordebugheapenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
