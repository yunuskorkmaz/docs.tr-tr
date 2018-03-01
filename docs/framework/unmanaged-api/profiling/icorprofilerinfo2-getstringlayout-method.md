---
title: ICorProfilerInfo2::GetStringLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout Metodu
Bir dize nesnesi düzeni hakkındaki bilgileri alır. Bu yöntem de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ve yerine geçen [Icorprofilerınfo3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBufferLengthOffset`  
 [out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi. Uzunluk olarak saklanan bir `DWORD`.  
  
> [!NOTE]
>  Bu parametre dize uzunluğu kendisini arabelleği uzunluğunu döndürür. Arabelleğin uzunluğu artık kullanılamıyor.  
  
 `PStringLengthOffset`  
 [out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi. Uzunluk olarak saklanan bir `DWORD`.  
  
 `pBufferOffset`  
 [out] Bağıntı arabellek uzaklığı bir işaretçi `ObjectID` geniş karakter dizesi depolayan işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStringLayout` Yöntemi göreli uzaklıkları alır `ObjectID` aşağıdaki depolandığı konumun işaretçi:  
  
-   Dizesinin arabellek uzunluğu.  
  
-   Dize uzunluğu.  
  
-   Geniş karakterler gerçek dizesi içeren bir arabellek.  
  
 Null ile sonlandırılmış dizeler olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
