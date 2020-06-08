---
title: ICorProfilerInfo4::GetObjectSize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: b605419a291f7bee76ecad7e07be9a7a989f9fe9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496015"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 Yöntemi
Belirtilen nesnenin boyutunu döndürür. [ICorProfilerInfo:: GetObjectSize](icorprofilerinfo-getobjectsize-method.md) yöntemini, içinde belirtilebilenden daha büyük nesnelerin raporlama boyutlarına göre değiştirir `ULONG` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 'ndaki Nesnenin KIMLIĞI.  
  
 `pcSize`  
 dışı Nesnenin boyutunun bayt cinsinden işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Aynı türdeki farklı nesneler genellikle aynı boyutta olur. Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
