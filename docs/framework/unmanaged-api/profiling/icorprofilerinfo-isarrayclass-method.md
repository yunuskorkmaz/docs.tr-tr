---
title: ICorProfilerInfo::IsArrayClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: a6e483d820d183afc8ba6a68fc4635730ffd1e51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869344"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass Yöntemi
Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 'ndaki İnceedilecek sınıfın KIMLIĞI.  
  
 `pBaseElemType`  
 dışı Dizi öğelerinin türünü gösteren CorElementType numaralandırması değerine yönelik bir işaretçi.  
  
 `pBaseClassId`  
 dışı Kullanılabilir olduğunda dizi öğelerinin sınıf KIMLIĞINE yönelik bir işaretçi.  
  
 `pcRank`  
 dışı Dizinin derecesini (yani boyut sayısını) gösteren bir tamsayı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen sınıf bir dizi sınıfınse `IsArrayClass` yöntemi, null olmayan herhangi bir çıkış parametresi için bir S_OK HRESULT ve değerleri döndürür. Aksi takdirde, S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
