---
title: ICorProfilerInfo2::GetStringLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a3d26a99844d00609b28eaef08ff0874a6701fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664961"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout Yöntemi
Bir dize nesnesinin düzeni hakkındaki bilgileri alır. Bu metot kullanımdan kaldırılmıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ve yerine geçen [Icorprofilerınfo3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pBufferLengthOffset`  
 [out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi. Uzunluğu olarak depolanan bir `DWORD`.  
  
> [!NOTE]
>  Bu parametre, dizenin uzunluğu kendisi değil arabellek uzunluğunu döndürür. Arabellek uzunluğu artık kullanılamıyor.  
  
 `PStringLengthOffset`  
 [out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi. Uzunluğu olarak depolanan bir `DWORD`.  
  
 `pBufferOffset`  
 [out] Göreli yolu arabellek uzaklığı için bir işaretçi `ObjectID` geniş karakter dizesini depolayan bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStringLayout` Yöntemi göreli uzaklıkları alır `ObjectID` işaretçisinin konumları aşağıdaki depolanır:  
  
- Dizenin arabellek uzunluğu.  
  
- Dize uzunluğu.  
  
- Gerçek geniş karakter dizesini içeren arabellek.  
  
 Null ile sonlandırılmış dizeler olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
