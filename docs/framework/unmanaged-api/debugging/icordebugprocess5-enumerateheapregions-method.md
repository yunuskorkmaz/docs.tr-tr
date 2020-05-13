---
title: ICorDebugProcess5::EnumerateHeapRegions Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 50b0859d6727a25906f2c8b0f3fe96da228ab886
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213562"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions Yöntemi
Yönetilen yığının bellek aralıkları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppRegions`  
 dışı Nesnelerin yönetilen yığında bulunduğu bellek aralıklarına yönelik bir Numaralandırıcı olan [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi çağırmadan önce `ICorDebugProcess5::EnumerateHeapRegions` , [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve `areGCStructuresValid` döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin alanının değerini inceleyerek, atık toplama yığınının geçerli durumunda sıralanabilir olduğundan emin olmanız gerekir. Ayrıca, yöntemi, `ICorDebugProcess5::EnumerateHeapRegions` `E_FAIL` bellek bölgelerini oluşturmadan önce, işlemin kullanım ömrü içinde çok erken bir şekilde iliştirse de döndürülür.  
  
 Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez. [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.  
  
 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](cor-segment-structure.md) nesneleri Listeletmanızı sağlayan ıcorı, genum arabiriminden türetilmiş standart bir Numaralandırıcı. Her [cor_segment](cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı hakkında, bu kesimdeki nesnelerin nestiyle birlikte bilgi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
