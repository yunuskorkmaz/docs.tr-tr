---
title: ICorProfilerInfo2::GetContextStaticAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress Metodu
Belirtilen bağlamı kapsamında belirtilen bağlam statik alan için adresi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] İstenen içerik statik alan içeren sınıf kimliği.  
  
 `fieldToken`  
 [in] İstenen içerik statik alan için meta veri belirteci.  
  
 `contextId`  
 [in] İstenen içerik statik alan kapsamı bağlam kimliği.  
  
 `ppAddress`  
 [out] Belirtilen bağlamı içinde statik alanındaki adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetContextStaticAddress` Yöntemi döndürebilir şunlardan biri:  
  
-   Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.  
  
-   Çöp toplama yığınında olabilir nesneleri adresleri. Çöp toplama sonra profil oluşturucular geçerli varsayımında bulunmamalıdır şekilde bu adresleri çöp toplama sonra geçersiz hale gelebilir.  
  
 Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetContextStaticAddress` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Icorprofilerınfo2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
