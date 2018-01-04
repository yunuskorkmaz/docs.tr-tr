---
title: ICorProfilerInfo2::GetRVAStaticAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetRVAStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4320ed3cdd3d17932d03e98d4d35d27adad2532a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress Metodu
Belirtilen göreli sanal adres (RAV) statik alan adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] İstenen RVA statik alan içeren sınıf kimliği.  
  
 `fieldToken`  
 [in] İstenen RVA statik alan için meta veri belirteci.  
  
 `ppAddress`  
 [out] RVA statik alan adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRVAStaticAddress` Yöntemi döndürebilir şunlardan biri:  
  
-   Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.  
  
-   Çöp toplama yığınında olabilir nesneleri adresleri. Çöp toplama sonra profil oluşturucular geçerli varsayımında bulunmamalıdır şekilde bu adresleri çöp toplama sonra geçersiz hale gelebilir.  
  
 Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetRVAStaticAddress` statik alanları bazıları zaten başlatılmış ve atık toplama nesneleri kök dizini değiştirme ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
