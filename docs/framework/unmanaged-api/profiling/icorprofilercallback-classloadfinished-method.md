---
title: ICorProfilerCallback::ClassLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cab4b039d225f4ee1b00add6ffec63fd35be8857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202813"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished Yöntemi
Profil Oluşturucu, bir sınıf yükleme işleminin tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 [in] Yüklenen sınıfı tanımlar.  
  
 `hrStatus`  
 [in] Sınıf başarıyla yüklü olup olmadığını gösteren bir HRESULT.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerini `classId` kadar bir bilgi isteği için geçerli değil `ClassLoadFinished` yöntemi çağrılır.  
  
 Sınıf yükleme bazı bölümleri sonra devam edebilir `ClassLoadFinished` geri çağırma. Bir hata HRESULT içinde `hrStatus` hata gösterir. Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü sınıfı yükleme işleminin başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
