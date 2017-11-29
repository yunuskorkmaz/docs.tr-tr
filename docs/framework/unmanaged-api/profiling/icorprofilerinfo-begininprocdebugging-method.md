---
title: "ICorProfilerInfo::BeginInprocDebugging Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.BeginInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c7c0b3c0a20c98b9ca2e5dd5ea51053008e415a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging Yöntemi
Başlatır hata ayıklama desteği işlemdeki. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fThisThreadOnly`  
 [in] Bu değer ayarlanırsa `true` yalnızca geçerli iş parçacığının için; hata ayıklama desteği başlatılamıyor ayarlamak `false` tüm iş parçacıklarının hata ayıklama desteği başlatılamıyor.  
  
 `pdwProfilerContext`  
 [out] Hata ayıklama oturumu tanımlayan döndürülen değer yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR hata ayıklama hizmetleri sınırlı işlemdeki .NET Framework sürüm 1.0 ve 1.1 debugging desteklenir. İşlem içi hata ayıklama hata ayıklama API'si denetleme bölümlerini kullanmak bir profil oluşturucu etkin. Ancak, müşteri geri bildirimi nedeniyle işlem içi hata ayıklama algıladı .NET Framework sürüm 2.0 kaldırıldı ve profil oluşturma API uygun olarak daha fazla işlevselliği kümesiyle değiştirildi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümü:** 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
