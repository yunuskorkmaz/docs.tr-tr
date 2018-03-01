---
title: ICorProfilerInfo2::GetThreadStaticAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1de945d2e6e0dd1ce3fa2da99e265bc304d4f4fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress Metodu
Belirtilen iş parçacığı kapsamında belirtilen statik iş parçacığı alan adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] İstenen iş parçacığı statik alan içeren sınıf kimliği.  
  
 `fieldToken`  
 [in] İstenen iş parçacığı statik alan için meta veri belirteci.  
  
 `threadId`  
 [in] İstenen statik alanın kapsamı iş parçacığı kimliği.  
  
 `ppAddress`  
 [out] Belirtilen iş parçacığı içinde statik alan adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetThreadStaticAddress` Yöntemi döndürebilir şunlardan biri:  
  
-   Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.  
  
-   Çöp toplama yığınında olabilir nesneleri adresleri. Bu adresler çöp toplama sonra geçersiz hale gelebilir bunu atık toplama profil oluşturucular geçerli varsayımında bulunmamalıdır sonra.  
  
 Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetThreadStaticAddress` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
