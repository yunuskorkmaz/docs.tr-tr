---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetThreadStaticAddress yöntemi'
title: ICorProfilerInfo2::GetThreadStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: bab4190f3751967031806dccbea2fdf6add73f6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647061"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress Yöntemi

Belirtilen iş parçacığının kapsamındaki belirtilen thread-static alanının adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a>Parametreler  

 `classId`  
 'ndaki İstenen iş parçacığı-statik alanını içeren sınıfın KIMLIĞI.  
  
 `fieldToken`  
 'ndaki İstenen iş parçacığı-statik alanı için meta veri belirteci.  
  
 `threadId`  
 'ndaki İstenen statik alan için kapsam olan iş parçacığının KIMLIĞI.  
  
 `ppAddress`  
 dışı Belirtilen iş parçacığı içindeki statik alanın adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetThreadStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:  
  
- Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.  
  
- Çöp toplama yığınında olabilecek nesnelerin adresleri. Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu yüzden çöp toplama profil oluşturucular sonra geçerli olduğunu varsaymamalıdır.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetThreadStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
