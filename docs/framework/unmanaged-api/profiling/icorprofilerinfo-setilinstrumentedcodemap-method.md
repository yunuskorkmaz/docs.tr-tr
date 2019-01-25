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
ms.openlocfilehash: d4780242dc34f31ecd0ff0dc2c339cdaa30278a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721168"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
Belirtilen Microsoft Ara dil (MSIL) map girişleri kullanarak belirtilen işlev için kod Haritası ayarlar.  
  
> [!NOTE]
>  Çağırma .NET Framework sürüm 2.0 `SetILInstrumentedCodeMap` üzerinde bir `FunctionID` genel işlev belirli uygulama etki alanında temsil eder, bu işlevin uygulama etki alanındaki tüm örnekleri etkiler.  
  
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
 [in] Kod Haritası ayarlanacağı işlevi kimliği.  
  
 `fStartJit`  
 [in] Belirten Boolean bir değer olup olmadığını çağrısı `SetILInstrumentedCodeMap` yöntemidir, belirli bir ilk `FunctionID`. Ayarlama `fStartJit` için `true` yapılan ilk çağrıda `SetILInstrumentedCodeMap` için bir verilen `FunctionID`ve `false` tutarında ücret alınır.  
  
 `cILMapEntries`  
 [in] İçindeki öğelerin sayısını `cILMapEntries` dizisi.  
  
 `rgILMapEntries`  
 [in] Bir dizi cor_ıl_map yapılarının her biri bir MSIL uzaklığını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu, kaynak kodundaki deyimleri bir yöntemin genellikle bu yöntem (örneğin, belirtilen kaynak satırı ulaşıldığında bildirmek için) izleme için ekler. `SetILInstrumentedCodeMap` özgün MSIL yönergeleri yeni konumlarına eşlemek bir profil oluşturucunun sağlar. Bir profil oluşturucu kullanabilirsiniz [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) özgün MSIL uzaklığı için belirli bir yerel uzaklık almak için yöntemi.  
  
 Hata ayıklayıcı, her eski uzaklığı bir MSIL içindeki özgün, değiştirilmemiş MSIL kod uzaklığı için ifade eder ve her yeni uzaklık yeni, izleme eklenmiş kod içinde MSIL uzaklığı başvurduğu varsayar. Harita, artan düzende sıralanmalıdır. Düzgün çalışması için atlamak için aşağıdaki yönergeleri izleyin:  
  
-   İzleme eklenmiş MSIL kodu yeniden değil.  
  
-   Özgün MSIL kodunu kaldırmayın.  
  
-   Program veritabanı (PDB) dosyasındaki dizi noktalarını girişlerinde haritada içerir. Harita eksik girdiler enterpolasyon değil. Bu nedenle, aşağıdaki harita verilen:  
  
     (0 eski, 0 yeni)  
  
     (5 eski, 10 yeni)  
  
     (9 eski, 20 yeni)  
  
    -   Yeni Uzaklık 0, 0, 1, 2, 3 veya 4 eski bir uzaklık eşleştirilir.  
  
    -   Eski bir uzaklık 5, 6, 7 veya 8, 10 yeni uzaklık eşleştirilir.  
  
    -   9 veya daha eski bir uzaklık yeni uzaklık 20 eşleştirilir.  
  
    -   Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleştirilir.  
  
    -   Yeni bir uzaklık 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklığı 5 eşleştirilir.  
  
    -   20 veya üzeri bir yeni uzaklığı eski uzaklığı 9 eşleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
