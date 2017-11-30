---
title: "ICorDebugProcess5::EnumerateHeap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41cd7d47650cdfe6a3598ba126be489107181a44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap Yöntemi
Bir numaralandırıcı nesneleri yönetilen yığında alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppObject`  
 [out] Adresine bir işaretçi bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) yönetilen öbek üzerinde bulunan nesneleri için bir numaralandırıcı arabirimi nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırmadan önce `ICorDebugProcess5::EnumerateHeap` yöntemi çağırın [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini inceleyin `areGCStructuresValid` dönen alan [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Çöp toplama yığın mevcut durumunda numaralandırılabilir olduğundan emin olmak için nesne. Ayrıca, `ICorDebugProcess5::EnumerateHeap` döndürür `E_FAIL` yönetilen yığında ayrılan için bellek önce işlem ömrü içinde çok erken eklediğiniz durumunda.  
  
 [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) arabiriminin nesnesidir Numaralandırılacak izin veren Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri. Bu yöntem doldurur [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) koleksiyon nesnesi ile [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) tüm nesneler hakkında bilgi sağlayan örnekleri. Koleksiyon ayrıca içerebilir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) tarafından olsunlar olmayan nesneler hakkında bilgi sağlayan örnekleri nesne ancak henüz atık toplayıcısı tarafından toplanan değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugprocess5 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
