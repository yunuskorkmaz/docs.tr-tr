---
title: ICorDebugGCReferenceEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416809"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next Yöntemi
Belirtilen sayıda alır [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olacak nesneleri hakkında bilgi içeren örnekleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 celt  
 [in] Alınacak kökleri sayısı.  
  
 kökler  
 [out] Her biri işaret işaretçileri, bir dizi bir [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) çöpünün toplanma olması için bir nesne kökünü temsil eden nesne.  
  
 pceltFetched  
 [out] Sayısını gösteren bir işaretçi [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) gerçekte döndürülen nesneleri `roots`. Bu değer olabilir `null` varsa `celt` 1'dir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugGCReferenceEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
