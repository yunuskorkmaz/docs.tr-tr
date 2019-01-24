---
title: ICorProfilerModuleEnum::GetCount Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0d386dfa3e3ad8d60e239c82a84c648f2813696
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572061"
---
# <a name="icorprofilermoduleenumgetcount-method"></a>ICorProfilerModuleEnum::GetCount Metodu
Uygulamaya yüklenen yönetilen modülleri sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [out] Çalışma zamanı modülleri koleksiyon sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerModuleEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
