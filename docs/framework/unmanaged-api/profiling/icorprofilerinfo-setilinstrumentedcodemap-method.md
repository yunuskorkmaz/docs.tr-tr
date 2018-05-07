---
title: ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ecb80de1ae46b072df4bab8357e78e7a22ae298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
Kod Haritası belirtilen Microsoft Ara dili (MSIL) harita girişleri kullanarak belirtilen işlev için ayarlar.  
  
> [!NOTE]
>  Çağırma .NET Framework sürüm 2.0, `SetILInstrumentedCodeMap` üzerinde bir `FunctionID` genel bir belirli uygulama etki alanı işlev temsil eder Bu işlev uygulama etki alanındaki tüm örneklerini etkiler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kod Haritası ayarlanacak işlevi kimliği.  
  
 `fStartJit`  
 [in] Gösteren bir Boole değeri olup olmadığını çağrısı `SetILInstrumentedCodeMap` yöntemdir belirli bir ilk `FunctionID`. Ayarlama `fStartJit` için `true` yapılan ilk çağrıda `SetILInstrumentedCodeMap` için bir verilen `FunctionID`ve `false` bundan sonra.  
  
 `cILMapEntries`  
 [in] Öğe sayısı `cILMapEntries` dizi.  
  
 `rgILMapEntries`  
 [in] Her biri bir MSIL uzaklığını belirtir dizisi cor_ıl_map yapıların.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu kaynak kodundaki deyimleri yönteminin bu yöntem (örneğin, belirtilen kaynak satırı ulaşıldığında bildirmek için) izlemek için genellikle ekler. `SetILInstrumentedCodeMap` Yeni konumlarını özgün MSIL yönergeleri eşlemek bir profil oluşturucu sağlar. Bir profil oluşturucu kullanabilirsiniz [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) özgün MSIL uzaklığı için belirli bir yerel uzaklığı almak için yöntemi.  
  
 Hata ayıklayıcı her eski uzaklığı içindeki özgün, değiştirilmemiş MSIL kod uzaklığı MSIL başvurduğu ve her yeni uzaklığı yeni, Araçlı kodundaki MSIL uzaklığı başvurduğu varsayar. Harita artan düzende sıralanmış. Atlama için düzgün çalışması için aşağıdaki yönergeleri izleyin:  
  
-   İzleme eklenmiş MSIL kodu yeniden değil.  
  
-   Özgün MSIL kodunu kaldırmayın.  
  
-   Program veritabanı (PDB) dosyasından tüm sıralama noktaları girişlerinde eşlemesinde içerir. Harita eksik girdiler kesinti değil. Bu nedenle, aşağıdaki harita verilen:  
  
     (0 eski, 0 yeni)  
  
     (5 eski, 10 yeni)  
  
     (9 eski, 20 yeni)  
  
    -   0, 1, 2, 3 veya 4 eski uzaklığı yeni uzaklığı 0 eşleşecektir.  
  
    -   5, 6, 7 veya 8 eski uzaklığı yeni uzaklık 10 eşleşecektir.  
  
    -   9 veya üzeri eski uzaklığı yeni uzaklık 20 eşleşecektir.  
  
    -   Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleşecektir.  
  
    -   Yeni uzaklığını 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklık 5 eşleşecektir.  
  
    -   Yeni bir uzaklık 20 veya daha yüksek eski uzaklık 9 eşleşecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
