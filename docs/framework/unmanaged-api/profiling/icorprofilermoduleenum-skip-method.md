---
description: ': ICorProfilerModuleEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerModuleEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: 4d814e5e9e369fe286b471fadc9675345cfb5b94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798972"
---
# <a name="icorprofilermoduleenumskip-method"></a>ICorProfilerModuleEnum::Skip Yöntemi

Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki Atlanacak öğe sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt` öğeler atlandı.|  
|S_FALSE|Daha az öğe olmadığını `celt` belirten öğe atlandı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu Numaralandırıcı imlecinizin yeni konumu (geçerli konum) + ' dır `celt` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerModuleEnum Arabirimi](icorprofilermoduleenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
