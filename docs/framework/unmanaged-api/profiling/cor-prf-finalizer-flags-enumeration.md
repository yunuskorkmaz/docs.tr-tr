---
title: "COR_PRF_FINALIZER_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FINALIZER_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FINALIZER_FLAGS
helpviewer_keywords: COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 63707ca18be29555919264f9aa3a0f143efdd374
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corprffinalizerflags-enumeration"></a>COR_PRF_FINALIZER_FLAGS Numaralandırması
Bir nesne için sonlandırıcıyı açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|Sonlandırıcıyı önemlidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_FINALIZER_FLAGS` Numaralandırması tarafından kullanılan [Icorprofilercallback2::finalizeableobjectqueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) bir nesne için sonlandırıcıyı açıklamak için yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma numaralandırmaları](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
