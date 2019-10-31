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
ms.openlocfilehash: 3ab4da3fcf43731587dae6f3a8e82ea48c5ee1ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129637"
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
 dışı Nesnelerin yönetilen yığında bulunduğu bellek aralıklarına yönelik bir Numaralandırıcı olan [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugProcess5::EnumerateHeapRegions` yöntemi çağrılmadan önce, [ICorDebugProcess5:: GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metodunu çağırmanız ve döndürülen [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnesinin `areGCStructuresValid` alanının değerini inceleyerek, çöp toplama işleminin geçerli durum Numaralandırılabilir. Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi, işlem kullanım ömrü içinde çok erken iliştirmeye, bellek bölgeleri oluşturulmadan önce `E_FAIL` döndürür.  
  
 Bu yöntem, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırmak için garanti edilir, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez. [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) Collection nesnesi boş veya ayrılmış bellek bölgeleri içerebilir.  
  
 [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) Interface nesnesi, [cor_segment](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesnelerini Listeletmanızı sağlayan ıcorhata ayıklama genum arabiriminden türetilmiş standart bir Numaralandırıcı. Her [cor_segment](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesnesi, belirli bir segmentin bellek aralığı ve bu kesimdeki nesnelerin nestiyle birlikte hakkında bilgi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
