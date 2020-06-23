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
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904279"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next Yöntemi
Yönetilen yığının bellek bölgeleri hakkında bilgi içeren [cor_segment](cor-segment-structure.md) örneklerinin belirtilen sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 celt  
 'ndaki Alınacak parçaların sayısı.  
  
 segmentler  
 dışı Her biri yönetilen yığında bir bellek bölgesi hakkında bilgi sağlayan bir [cor_segment](cor-segment-structure.md) nesnesine işaret eden işaretçiler dizisi.  
  
 Pceltfettiz  
 dışı Aslında ' de döndürülen [cor_segment](cor-segment-structure.md) nesnelerinin sayısına yönelik bir işaretçi `segments` . Bu değer 1 ise `null` olabilir `celt` .  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapSegmentEnum Arabirimi](icordebugheapsegmentenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
