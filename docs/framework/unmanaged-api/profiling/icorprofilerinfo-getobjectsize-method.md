---
title: ICorProfilerInfo::GetObjectSize Yöntemi
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
ms.openlocfilehash: cd337ca6d7b03ad22f178c9c7084cfa2585da73c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782743"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize Yöntemi
Belirtilen nesnenin boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesnenin kimliği.  
  
 `pcSize`  
 [out] Nesnenin boyutu, bayt için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem artık kullanılmıyor. COR_E_OVERFLOW nesneler için 4 GB değerinden 64-bit platformlarda döndürür. Kullanım [Icorprofilerınfo4::getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) yöntemi yerine.  
  
 Aynı türden farklı nesneler genellikle aynı boyuta sahip. Ancak, diziler veya dizeler gibi bazı türleri her nesne için başka bir boyutu olabilir.  
  
 Tarafından döndürülen boyutla `GetObjectSize` yöntemi nesnenin çöp koleksiyonu yığınında sonra oluşabilecek herhangi bir hizalama doldurmaya içermez. Kullanırsanız `GetObjectSize` nesne başka bir nesnenin çöp koleksiyonu yığınında ilerlemek için yöntemi el ile gerektiği şekilde doldurma hizalama ekleyin.  
  
- 32 bit Windows üzerinde COR_PRF_GC_GEN_0 COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalaması kullanın ve 8 baytlık hizalama COR_PRF_GC_LARGE_OBJECT_HEAP kullanır.  
  
- 64 bit Windows üzerinde hizalama her zaman 8 bayt'tır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
