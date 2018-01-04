---
title: ICorProfilerInfo2::GetBoxClassLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ef6df997a4ba4369b87789e47ac7ead2206162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a>ICorProfilerInfo2::GetBoxClassLayout Metodu
Bu kutu içinde belirtilen değer türü bulunduğu hakkında bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] Kutulu değer türü açıklanır sınıfı kimliği.  
  
 `pBufferOffset`  
 [out] Değer türü sarmalanmış nesne kimliği işaretçisi göre uzaklığı bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 `pBufferOffset` Değer, değer türü kutusu içinde konumdur. Sonra `pBufferOffset` uygulanan bir Kutulu nesnesine değer türünün sınıf düzeni nesnenin değeri yorumlamak için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
