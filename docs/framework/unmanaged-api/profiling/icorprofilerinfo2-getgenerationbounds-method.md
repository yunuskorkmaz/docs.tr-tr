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
ms.openlocfilehash: 2e6e3a6432d6568532a5f5b9676b5f130eb83d0b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502900"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds Yöntemi
Yığın kesimleri olan bellek bölgelerini alır, bu, çeşitli çöp toplama nesilleri yapar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cObjectRanges`  
 'ndaki Dizi için çağıran tarafından ayrılan öğe sayısı `ranges` .  
  
 `pcObjectRanges`  
 dışı Dizide döndürülecek bir veya hepsi olan toplam Aralık sayısını belirten bir tamsayı işaretçisi `ranges` .  
  
 `ranges`  
 dışı Her biri çöp toplama yapılmakta olan kuşak içindeki belleğin bir aralığını (yani bloğunu) açıklayan [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) yapıları dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetGenerationBounds`Çöp toplama işlemi devam ettiğinden, yöntemi herhangi bir profil oluşturucu geri çağrısından çağrılabilir.

 Nesklerde en fazla kaydırma, çöp koleksiyonları sırasında gerçekleşir. Nesiller koleksiyonlar arasında büyüyebilir ancak genellikle hareket etmez. Bu nedenle, çağrının en ilginç yerleri `GetGenerationBounds` ve ' dir `ICorProfilerCallback2::GarbageCollectionStarted` `ICorProfilerCallback2::GarbageCollectionFinished` .  
  
 Program başlatma sırasında bazı nesneler ortak dil çalışma zamanı (CLR) tarafından genellikle 2. nesil 3 ve 0 ' da ayrılır. Bu nedenle, yönetilen kodun yürütülmeye başladığı zaman, bu nesiller de nesneleri içerecektir. Atık toplayıcı tarafından oluşturulan kukla nesneler dışında, 1 ve 2. nesil normalde boş olur. (Kukla nesnelerin boyutu, CLR 'nin 32 bitlik uygulamalarında 12 bayttır; boyut 64 bit uygulamalarda daha büyüktür.) Ayrıca, yerel görüntü Oluşturucu (NGen. exe) tarafından üretilen modüller içindeki 2. nesil aralıkları görebilirsiniz. Bu durumda, kuşak 2 ' deki nesneler, çöp toplayıcı tarafından değil NGen. exe çalıştırıldığında ayrılan *dondurulmuş nesnelerdir*.  
  
 Bu işlev, arayana ayrılan arabellekleri kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
