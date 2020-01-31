---
title: ICorProfilerInfo2::GetContextStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868687"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress Yöntemi
Belirtilen bağlamın kapsamındaki belirtilen context-static alanı için adresi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 'ndaki İstenen bağlam-statik alanını içeren sınıfın KIMLIĞI.  
  
 `fieldToken`  
 'ndaki İstenen bağlam-statik alanı için meta veri belirteci.  
  
 `contextId`  
 'ndaki İstenen bağlam-statik alanı için kapsam olan bağlamın KIMLIĞI.  
  
 `ppAddress`  
 dışı Belirtilen bağlam içindeki statik alanın adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetContextStaticAddress` yöntemi aşağıdakilerden birini döndürebilir:  
  
- Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.  
  
- Çöp toplama yığınında olabilecek nesnelerin adresleri. Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce, statik alanlardan bazıları zaten başlatılmış ve atık toplama nesnelerini kök halinde kullanıma sunabilse de `GetContextStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
