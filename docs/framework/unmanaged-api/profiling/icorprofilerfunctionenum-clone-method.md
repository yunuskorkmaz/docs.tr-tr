---
title: ICorProfilerFunctionEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: d6f348eb781efdef89926ec1bc267281bf3a5004
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503113"
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone Yöntemi
Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı Bu [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisinin bir işaretçisi. Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar. Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionEnum Arabirimi](icorprofilerfunctionenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
