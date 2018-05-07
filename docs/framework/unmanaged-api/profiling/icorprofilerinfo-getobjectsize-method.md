---
title: ICorProfilerInfo::GetObjectSize Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ed27602dfa9090b46b842e4e65af8af373cc207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize Metodu
Belirtilen nesnenin boyutu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesne kimliği.  
  
 `pcSize`  
 [out] Nesnenin boyutu, bayt gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem artık kullanılmıyor. Bu COR_E_OVERFLOW nesneler için 4 GB'den büyük 64 bit platformlarda döndürür. Kullanım [Icorprofilerınfo4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) yöntemi yerine.  
  
 Aynı türden farklı nesneler genellikle aynı boyuta sahip. Bununla birlikte, dizi veya dize gibi bazı türleri her nesne için farklı bir boyut olabilir.  
  
 Tarafından döndürülen boyutu `GetObjectSize` yöntemi nesnesi atık toplama yığında alındıktan sonra oluşabilecek herhangi bir hizalama doldurmaya içermez. Kullanırsanız `GetObjectSize` atık toplama yığında nesne başka bir nesnenin ilerletileceği yöntemi gerektiği gibi el ile doldurma hizalama ekleyin.  
  
-   32 bit Windows COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4-bayt hizalama ve COR_PRF_GC_LARGE_OBJECT_HEAP 8-bayt hizalama kullanır.  
  
-   64 bit Windows'ta hizalama her zaman 8 bayt'tır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
