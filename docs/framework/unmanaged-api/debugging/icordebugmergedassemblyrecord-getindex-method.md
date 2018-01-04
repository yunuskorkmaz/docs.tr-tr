---
title: "ICorDebugMergedAssemblyRecord::GetIndex yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ff8d6935f5507ab02d9d566921cb7f8a890bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>ICorDebugMergedAssemblyRecord::GetIndex yöntemi
Derlemenin ön eki dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pIndex`  
 [out] Önek dizin için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Önek dizin birleştirilmiş meta verileri tür adları ad çakışmaları önlemek için kullanılır.  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMergedAssemblyRecord Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
