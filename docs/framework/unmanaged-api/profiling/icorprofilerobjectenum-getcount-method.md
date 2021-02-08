---
description: ': ICorProfilerObjectEnum:: GetCount yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerObjectEnum::GetCount Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: b1bedfca913a099f88780807021497d15f75fcd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798946"
---
# <a name="icorprofilerobjectenumgetcount-method"></a>ICorProfilerObjectEnum::GetCount Yöntemi

Koleksiyondaki dondurulmuş nesnelerin toplam sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pcelt`  
 dışı Koleksiyondaki dondurulmuş nesne sayısına yönelik bir işaretçi.  
  
 Bu yöntem, .NET Framework sürüm 3,5 hizmet paketi 1 (SP1) ve sonraki sürümlerde her zaman sıfır döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerObjectEnum Arabirimi](icorprofilerobjectenum-interface.md)
