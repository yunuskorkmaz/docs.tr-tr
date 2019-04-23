---
title: ICorProfilerCallback::ModuleLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 354d2f278bcb0618b823b7300079278fc4c3315c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157358"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished Yöntemi
Profil Oluşturucu, bir modül yükleme işleminin tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Yükleme Tamamlandı modül kimliği.  
  
 `hrStatus`  
 [in] Modül başarıyla yüklendi gösteren HRESULT.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerini `moduleId` kadar bir bilgi isteği için geçerli değil `ModuleLoadFinished` yöntemi çağrılır.  
  
 Modül yükleme bazı bölümleri sonra devam edebilir `ModuleLoadFinished` geri çağırma. Bir hata HRESULT içinde `hrStatus` hata gösterir. Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü Modül yükleme işleminin başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
