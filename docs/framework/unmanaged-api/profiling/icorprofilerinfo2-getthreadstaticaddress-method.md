---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8c18935069e4162236f99c411312087ce73bdc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782214"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress Yöntemi
Belirtilen iş parçacığı kapsamında belirtilen statik iş parçacığı alanı adresini alır.  
  
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
 [in] İstenen iş parçacığı statik alanı içeren sınıf kimliği.  
  
 `fieldToken`  
 [in] İstenen iş parçacığı statik alan için meta veri belirteci.  
  
 `threadId`  
 [in] Kapsamı istenen statik alan için iş parçacığı kimliği.  
  
 `ppAddress`  
 [out] Belirtilen iş parçacığı içinde statik alanı adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetThreadStaticAddress` Yöntemi aşağıdakilerden birini döndürebilir:  
  
- Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanı belirtilen bağlam bir adres değil atandıysa HRESULT.  
  
- Adresleri nesnelerin çöp koleksiyonu yığınında olabilir. Çöp toplamanın ardından bu adresler geçersiz hale gelebilir bunu sonra atık toplama profil oluşturucular geçerli olduğunu varsayın değil.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetThreadStaticAddress` bazı statik alanlar zaten başlatılmış olabilir ancak tüm kendi statik alanları için CORPROF_E_DATAINCOMPLETE döndürür ve çöp toplama nesneleri kök dizini değiştirme.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
