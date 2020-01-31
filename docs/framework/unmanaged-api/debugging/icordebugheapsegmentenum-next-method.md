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
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777530"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next Yöntemi
Yönetilen yığının bellek bölgeleri hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 dışı Her biri yönetilen yığında bir bellek bölgesi hakkında bilgi sağlayan bir [cor_heapobject](cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.  
  
 Pceltfettiz  
 dışı Aslında `segments`döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi. Bu değer, `celt` 1 ise `null` olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapSegmentEnum Arabirimi](icordebugheapsegmentenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
