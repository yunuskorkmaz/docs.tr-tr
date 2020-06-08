---
title: ICorProfilerInfo3::GetStringLayout2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496379"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 Yöntemi
Bir dize nesnesinin yerleşimi hakkında bilgi alır. Bu yöntem [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) yönteminin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStringLengthOffset`  
 dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` . Uzunluk bir olarak depolanır `DWORD` .  
  
 `pBufferOffset`  
 dışı Geniş karakter dizesini depolayan işaretçiye bağlı olarak, arabelleğin uzaklığına yönelik bir işaretçi `ObjectID` .  
  
## <a name="remarks"></a>Açıklamalar  
 Dizeler null ile sonlandırılmış olabilir veya olmayabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
