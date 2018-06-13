---
title: ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bffe293f7d29c34a22196336533202996f3fd129
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454049"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi
Profil Oluşturucu ortak dil çalışma zamanı (CLR) profil oluşturucu DLL kaldırılmak üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri çağırma yönteminden döndürülen değer yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProfilerDetachSucceeded` Tüm iş parçacıklarının Profil Oluşturucu'nın kod çıkış sonra geri çağırma verildi. Profil Oluşturucu, bu yöntem çağrıldığında, kendi kullanıcı Arabirimi veya günlük bileşeni bildiren gibi kendi yıkıcı için uygun olmayan herhangi bir son dakika görevi gerçekleştirmeniz gerekir. Ancak, profil oluşturucu işlevler CLR tarafından bu geri çağırma sırasında sağlanan arabirimlerindeki çağırmamalıdır (gibi [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri).  
  
 CLR ayırma işlemi başarılı olduğunu göstermek için Windows uygulama olay günlüğünde bir giriş oluşturur.  
  
 Profil Oluşturucu ten bu geri döndükten sonra CLR Profil Oluşturucu nesne serbest bırakır ve profil oluşturucu DLL kaldırır. Bu nedenle, profil oluşturucu ten bu geri döndükten sonra DLL profil oluşturucu içinde gerçekleşmesi yürütme neden olacak herhangi bir eylem gerçekleştirmeniz gerekir değil. Örneğin, değil iş parçacığı oluşturabilir veya gerekir Zamanlayıcı geri aramaları kaydetme.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
