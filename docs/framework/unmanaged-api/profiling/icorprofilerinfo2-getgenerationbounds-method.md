---
title: ICorProfilerInfo2::GetGenerationBounds Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 310bde2889f8a383fde88cb1bbffce9bad157399
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267997"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds Yöntemi
Çeşitli çöp toplama kuşakları ' kılan yığın segmentler bellek bölgeleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cObjectRanges`  
 [in] Öğe için çağırıcı tarafından ayrılan sayısı `ranges` dizisi.  
  
 `pcObjectRanges`  
 [out] Bazı belirten aralıkları, toplam sayısı veya her biri, döndürülecek tamsayı işaretçisi `ranges` dizisi.  
  
 `ranges`  
 [out] Bir dizi [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları, çöp toplama aşamasında nesil içinde her biri açıklanmaktadır bellek aralığı (yani, blok).  
  
## <a name="remarks"></a>Açıklamalar  
 `GetGenerationBounds` Yöntemi koşuluyla atık toplama devam ederken değil herhangi bir profil oluşturucu geri çağrısından çağrılabilir.

 Çoğu kaydırma nesil atık toplama sırasında gerçekleşir. Nesil koleksiyonlar arasında büyüyebilir ancak genel olarak değiştirmemiz değil. Bu nedenle, en ilginç yerleri çağrılacak `GetGenerationBounds` bulunan `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Program açılışında, bazı nesneler ortak dil çalışma zamanı tarafından (CLR) kendisi, genellikle 3 ve 0 nesillerdeki ayrılır. Bu nedenle, yönetilen kod yürütülmeye başlamadan zaman, bu nesiller zaten nesnelerini içerecektir. Nesil 1 ve 2 normal çöp toplayıcısı tarafından oluşturulan işlevsiz nesneler dışında boş olur. (CLR'nin 32-bit uygulamalarında işlevsiz nesnelerin boyutunu 12 bayttır; 64-bit uygulamalarında boyutu büyük.) Native Image Generator (NGen.exe) tarafından üretilen modülleri içinde 2. nesil aralıklarını da görebilirsiniz. Bu durumda, 2. nesil nesneler olan *donmuş nesneler*, hangi ayrılır NGen.exe çalışırken yerine atık toplayıcı tarafından.  
  
 Bu işlev, arayana ayrılan arabellekler kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
