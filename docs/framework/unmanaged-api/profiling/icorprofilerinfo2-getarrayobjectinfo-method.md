---
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
ms.openlocfilehash: 839cd574e5352b74b47cd6242d5706bc6405d439
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862925"
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
 dışı Dizi için, C++ kurala göre düzenlendiği ham arabelleğin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `pDimensionSizes` ve `pDimensionLowerBounds` paralel dizilerdir, bu nedenle her dizide aynı dizinde bulunan öğeler aynı varlığın niteliklerinden oluşur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
