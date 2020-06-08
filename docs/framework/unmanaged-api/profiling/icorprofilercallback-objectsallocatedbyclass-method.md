---
title: ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 7176c0f88daad64f793131aca8c6d9fa592a878c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503282"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass Yöntemi
En son çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cClassCount`  
 'ndaki `classIds`Ve `cObjects` dizilerinin boyutu.  
  
 `classIds`  
 'ndaki Her KIMLIğIN bir veya daha fazla örneğe sahip bir sınıfı belirttiği sınıf kimlikleri dizisi.  
  
 `cObjects`  
 'ndaki Her tamsayı dizideki karşılık gelen sınıf için örnek sayısını belirten bir tamsayılar dizisi `classIds` .  
  
## <a name="remarks"></a>Açıklamalar  
 `classIds`Ve `cObjects` dizileri paralel dizilerdir. Örneğin, `classIds[i]` ve `cObjects[i]` aynı sınıfa başvur. Önceki çöp toplamadan bu yana bir sınıf örneği oluşturulmadıysa, sınıf atlanır. `ObjectsAllocatedByClass`Bu geri çağırma, büyük nesne yığınında ayrılan nesneleri rapor etmez.  
  
 Tarafından raporlanan sayılar `ObjectsAllocatedByClass` yalnızca tahminlerdir. Tam sayımlar için [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)kullanın.  
  
 `classIds`Karşılık gelen dizide kaldırma işlemi olan türler varsa dizi bir veya daha fazla null giriş içerebilir `cObjects` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
