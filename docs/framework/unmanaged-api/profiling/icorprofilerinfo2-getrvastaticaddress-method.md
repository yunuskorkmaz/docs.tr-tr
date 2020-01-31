---
title: ICorProfilerInfo2::GetRVAStaticAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: ca64d4f5932fb4a0c0486fee5ca1017a6d3adaf2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868635"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>ICorProfilerInfo2::GetRVAStaticAddress Metodu
Belirtilen göreli sanal adres (RVA) statik alanının adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 'ndaki İstenen RVA-statik alanını içeren sınıfın KIMLIĞI.  
  
 `fieldToken`  
 'ndaki İstenen RVA-statik alanı için meta veri belirteci.  
  
 `ppAddress`  
 dışı RVA-statik alanının adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRVAStaticAddress` yöntemi aşağıdakilerden birini döndürebilir:  
  
- Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.  
  
- Çöp toplama yığınında olabilecek nesnelerin adresleri. Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetRVAStaticAddress`, bazı statik alanlar zaten başlatılmış olabilir ve atık toplama nesnelerini kök olarak oluşturabilir, ancak tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
