---
title: ICorProfilerInfo3::GetThreadStaticAddress2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62dadf4f21022f8f425596cf5957891ed39effe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189189"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>ICorProfilerInfo3::GetThreadStaticAddress2 Yöntemi
Belirtilen iş parçacığı ve uygulama etki alanı kapsamı içinde belirtilen statik iş parçacığı alanı adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 [in] İstenen iş parçacığı statik alanı içeren sınıf kimliği.  
  
 `fieldToken`  
 [in] İstenen iş parçacığı statik alan için meta veri belirteci.  
  
 `appDomainId`  
 [in] Uygulama etki alanı kimliği.  
  
 `threadId`  
 [in] Kapsamı istenen statik alan için iş parçacığı kimliği.  
  
 `ppAddress`  
 [out] Belirtilen iş parçacığı içinde statik alanı adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetThreadStaticAddress2` Yöntemi aşağıdakilerden birini döndürebilir:  
  
-   Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanı belirtilen bağlam bir adres değil atandıysa HRESULT.  
  
-   Adresleri nesnelerin çöp koleksiyonu yığınında olabilir. Çöp toplamanın ardından, profil oluşturucular geçerli olduğunu varsayın değil için bu adresleri çöp toplamanın ardından geçersiz hale gelebilir.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetThreadStaticAddress2` bazı statik alanlar zaten başlatılmış olabilir ancak tüm kendi statik alanları için CORPROF_E_DATAINCOMPLETE döndürür ve çöp toplama nesneleri kök dizini değiştirme.  
  
 [Icorprofilerınfo2::getthreadstaticaddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) yöntemi benzer `GetThreadStaticAddress2` yöntemi, ancak bir uygulama etki alanı bağımsız değişkeni kabul etmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
