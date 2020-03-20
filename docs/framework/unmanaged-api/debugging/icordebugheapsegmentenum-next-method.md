---
title: ICorDebugHeapSegmentEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178889"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next Yöntemi
Yönetilen [yığının](cor-heapobject-structure.md) bellek bölgeleri hakkında bilgi içeren COR_HEAPOBJECT örneklerinin belirtilen sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 Celt  
 [içinde] Alınacak segment sayısı.  
  
 segmentler  
 [çıkış] Her biri yönetilen yığındaki bellek bölgesi hakkında bilgi sağlayan [bir COR_HEAPOBJECT](cor-heapobject-structure.md) nesneyi işaret eden bir dizi işaretçi.  
  
 pceltFetched  
 [çıkış] Gerçekte döndürülen [COR_HEAPOBJECT](cor-heapobject-structure.md) nesne sayısına `segments`işaretçi Bu değer `null` 1 `celt` ise olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapSegmentEnum Arabirimi](icordebugheapsegmentenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
