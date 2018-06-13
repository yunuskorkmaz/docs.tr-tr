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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b37c30df6467439d04e367e13b0fc4ffff0ec6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422952"
---
# <a name="icordebugobjectenumnext-method"></a>ICorDebugObjectEnum::Next Yöntemi
Geçerli konumdan başlayarak numaralandırması nesneleri belirtilen sayıdaki göreli sanal adresleri (RVAs) alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak nesne sayısı.  
  
 `objects`  
 [out] Her biri bir CORDB_ADDRESS nesnesine işaret eden bir dizi işaretçisi.  
  
 `pceltFetched`  
 [out] İşaretçi gerçekte döndürülen nesne sayısı. Bu değer null ise `celt` biridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
