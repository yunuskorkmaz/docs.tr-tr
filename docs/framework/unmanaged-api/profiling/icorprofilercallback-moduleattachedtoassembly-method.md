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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503399"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly Yöntemi
Profil oluşturucuyu bir modülün üst derlemesine iliştirilmekte olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 'ndaki İliştirilmekte olan modülün KIMLIĞI.  
  
 `AssemblyId`  
 'ndaki Modülün eklendiği üst derlemenin KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir modül bir içeri aktarma adres tablosu (ıAT) aracılığıyla, öğesine yapılan çağrısıyla `LoadLibrary` veya meta veri başvurusu aracılığıyla yüklenebilir. Sonuç olarak, ortak dil çalışma zamanı (CLR) yükleyicisinin, bir modülün yaşadığı derlemeyi belirlemek için birden çok kod yolu vardır. Bu nedenle, [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) çağrıldıktan sonra, modül içinde bulunduğu derlemeyi bilmez ve üst derleme kimliğini elde etmek mümkün değildir. `ModuleAttachedToAssembly`Yöntemi, modül üst derlemesine iliştirildiği zaman çağrılır ve üst derleme kimliği elde edilebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
