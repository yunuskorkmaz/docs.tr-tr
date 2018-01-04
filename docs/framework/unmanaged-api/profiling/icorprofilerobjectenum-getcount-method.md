---
title: ICorProfilerObjectEnum::GetCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.GetCount
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7675749a132cffe284d73bab3dba91f6ff7a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumgetcount-method"></a>ICorProfilerObjectEnum::GetCount Metodu
Koleksiyonda dondurulmuş nesne toplam sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcelt`  
 [out] Koleksiyondaki dondurulmuş nesne sayısı için bir işaretçi.  
  
 Bu yöntem her zaman sıfır .NET Framework sürüm 3.5 döndürülecek Service Pack 1 (SP1) ve sonraki sürümler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerObjectEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
