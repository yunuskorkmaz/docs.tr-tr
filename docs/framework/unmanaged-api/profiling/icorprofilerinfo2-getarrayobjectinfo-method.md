---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetArrayObjectInfo yöntemi'
title: ICorProfilerInfo2::GetArrayObjectInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 1427ad696f73d90a2a07698c71456571fb14ee70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760543"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo Metodu

Bir dizi nesnesi hakkında ayrıntılı bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parametreler  

 `objectId`  
 'ndaki Geçerli bir array nesnesinin KIMLIĞI.  
  
 `cDimensions`  
 'ndaki Dizinin derece (boyut sayısı).  
  
 `pDimensionSizes`  
 dışı Her biri dizi boyutunun boyutunu temsil eden tamsayılar içeren bir dizi.  
  
 `pDimensionLowerBounds`  
 dışı Her biri dizi boyutunun alt sınırını temsil eden tamsayılar içeren bir dizi.  
  
 `ppData`  
 dışı Dizi için, C++ kuralına göre düzenlendiği ham arabelleğin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `pDimensionSizes`Ve `pDimensionLowerBounds` paralel dizilerdir, bu nedenle her dizide aynı dizinde bulunan öğeler aynı varlığın nitelikleri olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
