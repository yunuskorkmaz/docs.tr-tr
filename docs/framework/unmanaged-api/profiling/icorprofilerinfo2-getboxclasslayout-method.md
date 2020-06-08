---
title: ICorProfilerInfo2::GetBoxClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 630b67a64716f26577bbc376970e4f76216f4da5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497362"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a>ICorProfilerInfo2::GetBoxClassLayout Yöntemi
Belirtilen değer türünün paketleniyorsa nerede bulunduğu hakkında bilgi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `classId`  
 'ndaki Kutulanmış değer türünü tanımlayan sınıfın KIMLIĞI.  
  
 `pBufferOffset`  
 dışı Değer türünün kutulanmış nesne KIMLIĞI işaretçisine göre göreli bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 `pBufferOffset`Değer, bir kutu içindeki değer türünün konumudur. `pBufferOffset`Kutulanmış bir nesneye uygulandıktan sonra, nesnenin değerini yorumlamak için değer türünün sınıf düzeni kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
