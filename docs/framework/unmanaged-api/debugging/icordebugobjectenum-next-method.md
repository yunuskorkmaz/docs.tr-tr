---
title: ICorDebugObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178697"
---
# <a name="icordebugobjectenumnext-method"></a>ICorDebugObjectEnum::Next Yöntemi
Geçerli konumdan başlayarak, belirtilen nesne sayısının göreli sanal adreslerini (RVAs) numaralandırmadan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 [içinde] Alınacak nesne sayısı.  
  
 `objects`  
 [çıkış] Her biri CORDB_ADDRESS bir nesneyi işaret eden bir dizi işaretçi.  
  
 `pceltFetched`  
 [çıkış] Gerçekte döndürülen nesne sayısına işaretçi. Bu değer, varsa `celt` null olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
