---
title: ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6b5281e30c48471131fa12e5106f7d0a6826e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452565"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi
Profil Oluşturucu bir modül kendi üst derlemeye bağlı olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] İliştirilmekte olan modül kimliği.  
  
 `AssemblyId`  
 [in] Modül bağlı olduğu üst derleme kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir modülü içeri aktarma adres tablosunu (IAT) bir çağrıyla yüklenebilir `LoadLibrary`, veya bir meta veri başvuru. Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisi, bir modül yaşadığı derleme belirlemek için birden çok kod yolları vardır. Bu nedenle, olası bundan sonra [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) çağrılır modülü hangi derleme bilmez olarak ve üst derleme kimliği alma mümkün değildir. `ModuleAttachedToAssembly` Modülü kendi üst derleme ve kimliği elde edilebilir kendi üst derleme iliştirildiğinde yöntemi çağrılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
