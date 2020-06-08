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
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497978"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize Yöntemi
Belirtilen nesnenin boyutunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 'ndaki Nesnenin KIMLIĞI.  
  
 `pcSize`  
 dışı Nesnenin boyutunun bayt cinsinden işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bu yöntem artık kullanılmıyor. 64-bit platformlarda 4.000'DEN büyük nesneler için COR_E_OVERFLOW döndürür. Bunun yerine [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) yöntemini kullanın.  
  
 Aynı türdeki farklı nesneler genellikle aynı boyutta olur. Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.  
  
 Yöntem tarafından döndürülen boyut, `GetObjectSize` nesne çöp toplama yığınında olduktan sonra görünebilen herhangi bir hizalama dolgusu içermez. `GetObjectSize`Çöp toplama yığınında nesnesinden nesneye ilerlemek için yöntemini kullanırsanız, gerektiğinde hizalama doldurmayı el ile ekleyin.  
  
- 32 bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalama kullanın ve COR_PRF_GC_LARGE_OBJECT_HEAP 8 baytlık hizalama kullanır.  
  
- 64 bit Windows üzerinde hizalama her zaman 8 bayttır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
