---
title: ICorProfilerInfo2::GetGenerationBounds Metodu
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
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c84be5d7e78c348c0368e9639a470a8fc60e2ca7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds Metodu
Heap öğesinin çeşitli atık toplama nesli yapmak kesimlerin bellek bölümlerinin alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cObjectRanges`  
 [in] İçin çağıran tarafından ayrılmış. öğe sayısı `ranges` dizi.  
  
 `pcObjectRanges`  
 [out] Tamsayı aralığı, toplam sayısı bazı belirtir veya bunların tümü de döndürülecek bir işaretçi `ranges` dizi.  
  
 `ranges`  
 [out] Bir dizi [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları, atık toplama yapılıyor nesil içinde her biri açıklanmaktadır bellek aralığı (yani, blok).  
  
## <a name="remarks"></a>Açıklamalar  
 `GetGenerationBounds` Yöntemi koşuluyla atık toplama devam değil tüm profil oluşturucu geri aramasından çağrılabilir. Diğer bir deyişle, onu arasında oluşan olanlar dışında herhangi bir geri aramadan çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Çoğu nesli kaydırma sırasında çöp koleksiyonları gerçekleşir. Nesli koleksiyonları arasında büyüyebilir ancak genellikle dolaşmak değil. Bu nedenle, çağırmak için en ilgi çekici yerleri `GetGenerationBounds` bulunan `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Program başlatma sırasında bazı nesneler ortak dil çalışma zamanı tarafından (CLR) kendisi, genellikle kuşakta 3 ve 0 ayrılır. Bu nedenle, yönetilen kod yürütme başlatılışında tarafından bu nesli zaten nesnelerini içerecektir. Nesil 1 ve 2 normalde atık toplayıcısı tarafından oluşturulan sahte nesneler dışında boş olacaktır. (Sahte nesneler 12 32-bit uygulamaları CLR bayt boyutudur; boyutu 64-bit uygulamalarında daha büyüktür.) Yerel Görüntü Oluşturucu (NGen.exe) tarafından üretilen modülleri içinde olduğunda 2. nesil aralıkları da görebilirsiniz. Bu durumda, 2. nesil nesneler olan *nesneleri dondurulmuş*, hangi ayrılır NGen.exe çalıştığında yerine atık toplayıcı tarafından.  
  
 Bu işlev, çağıran tarafından ayrılan arabellek kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
