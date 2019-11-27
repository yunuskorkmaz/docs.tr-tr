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
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433117"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds Yöntemi
Yığın kesimleri olan bellek bölgelerini alır, bu, çeşitli çöp toplama nesilleri yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cObjectRanges`  
 'ndaki `ranges` dizisi için çağıran tarafından ayrılan öğe sayısı.  
  
 `pcObjectRanges`  
 dışı `ranges` dizisinde döndürülecek bir veya hepsi olan toplam Aralık sayısını belirten bir tamsayı işaretçisi.  
  
 `ranges`  
 dışı Her biri çöp toplama yapılmakta olan kuşak içindeki belleğin bir aralığını (yani bloğunu) açıklayan [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çöp toplama işlemi devam ettiğinden, `GetGenerationBounds` yöntemi herhangi bir profil oluşturucu geri çağrısından çağrılabilir.

 Nesklerde en fazla kaydırma, çöp koleksiyonları sırasında gerçekleşir. Nesiller koleksiyonlar arasında büyüyebilir ancak genellikle hareket etmez. Bu nedenle, `GetGenerationBounds` çağrısı yapılacak en ilginç konumlar `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Program başlatma sırasında bazı nesneler ortak dil çalışma zamanı (CLR) tarafından genellikle 2. nesil 3 ve 0 ' da ayrılır. Bu nedenle, yönetilen kodun yürütülmeye başladığı zaman, bu nesiller de nesneleri içerecektir. Atık toplayıcı tarafından oluşturulan kukla nesneler dışında, 1 ve 2. nesil normalde boş olur. (Kukla nesnelerin boyutu, CLR 'nin 32 bitlik uygulamalarında 12 bayttır; boyut 64 bit uygulamalarda daha büyüktür.) Ayrıca, yerel görüntü Oluşturucu (NGen. exe) tarafından üretilen modüller içindeki 2. nesil aralıkları görebilirsiniz. Bu durumda, kuşak 2 ' deki nesneler, çöp toplayıcı tarafından değil NGen. exe çalıştırıldığında ayrılan *dondurulmuş nesnelerdir*.  
  
 Bu işlev, arayana ayrılan arabellekleri kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
