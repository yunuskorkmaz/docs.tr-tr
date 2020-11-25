---
title: ICorProfilerModuleEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ae9f6b7865a80e3edc4cae8fd1298e5eed864377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722836"
---
# <a name="icorprofilermoduleenumclone-method"></a>ICorProfilerModuleEnum::Clone Yöntemi

Bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppEnum`  
 dışı Sırasıyla bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisine yönelik bir işaretçi. Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar. Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerModuleEnum Arabirimi](icorprofilermoduleenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
