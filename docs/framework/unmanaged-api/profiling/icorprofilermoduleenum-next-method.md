---
title: ICorProfilerModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc33936735c40e2f30189066d80444b9fcb075ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671895"
---
# <a name="icorprofilermoduleenumnext-method"></a>ICorProfilerModuleEnum::Next Yöntemi
Belirtilen bitişik modül sayısı dizideki geçerli konum Numaralandırıcının başlayarak modüllerinin sıralı bir koleksiyonu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak modül sayısı.  
  
 `ids`  
 [out] Bir dizi `ModuleID` değerler, her biri alınan bir modülü temsil eder.  
  
 `pceltFetched`  
 [out] Gerçekte döndürülen öğe sayısına bir işaretçi `ids` dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`celt` öğeleri döndürülmedi.|  
|S_FALSE|Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerModuleEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
