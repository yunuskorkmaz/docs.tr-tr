---
description: ': ICorProfilerFunctionEnum:: GetCount metodu hakkında daha fazla bilgi edinin'
title: ICorProfilerFunctionEnum::GetCount Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: a3eccfa31676636aff7379b4080bcb85a268df6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737629"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a>ICorProfilerFunctionEnum::GetCount Metodu

Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 dışı Yüklenen işlevlerin sayısı.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerFunctionEnum Arabirimi](icorprofilerfunctionenum-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
