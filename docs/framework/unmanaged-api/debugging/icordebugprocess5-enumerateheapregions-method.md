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
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792398"
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
 `ICorDebugProcess5::EnumerateHeapRegions` yöntemi çağrılmadan önce, [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve döndürülen [COR_HEAPINFO](cor-heapinfo-structure.md) nesnesinin `areGCStructuresValid` alanının değerini inceleyerek geçerli durumunda çöp toplama yığınının numaralandırılanmış olduğundan emin olmanız gerekir. Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi, işlem kullanım ömrü içinde çok erken iliştirmeye, bellek bölgeleri oluşturulmadan önce `E_FAIL` döndürür.  
  
 Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez. [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.  
  
 [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](cor-segment-structure.md) nesneleri Listeletmanızı sağlayan ıcorı, genum arabiriminden türetilmiş standart bir Numaralandırıcı. Her [cor_segment](cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı hakkında, bu kesimdeki nesnelerin nestiyle birlikte bilgi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
