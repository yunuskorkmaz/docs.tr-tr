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
ms.openlocfilehash: 2608f91a7c5baa935e48fbe58ad4d14aaaad1f0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722511"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass Yöntemi

Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 Belirtilen sınıf bir dizi sınıfınse, `IsArrayClass` Yöntem bir S_OK HRESULT ve null olmayan herhangi bir çıkış parametresi için değerler döndürür. Aksi takdirde, S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
