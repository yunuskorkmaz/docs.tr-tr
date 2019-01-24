---
title: ICorDebugILCode2::GetInstrumentedILMap Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2abb24a319d8d3aff940ddb7eabd16b3e238862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611754"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bir harita Bu örnek için özgün yöntemi IL uzaklık profil oluşturucu izleme eklenmiş Ara dil (IL) uzaklıklarını döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 CMap  
 [in] Depolama kapasitesini `map` dizisi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 pcMap  
 [out] Eşleme dizisine yazılan cor_ıl_map değer sayısı.  
  
 map  
 [out] Eşleşmeleri profil oluşturucu izleme eklenmiş IL özgün metodun IL için bilgilerini cor_ıl_map değerleri dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu çağırarak eşleme ayarlarsa [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi, hata ayıklayıcı eşleme alınması ve eşleme, dahili olarak IL hesaplamak için yığın kaydırır kullanacağınız için bu yöntemi çağırabilir izlemeleri ve değişken yaşam süresi yok.  
  
 Varsa `cMap` 0'dır ve `pcMap` olan olmayan**null**, `pcMap` kullanılabilir cor_ıl_map değerlerinin bir sayıya ayarlayın. Varsa `cMap` sıfır olan depolama kapasitesini temsil ettiği `map` dizisi. Yöntem döndürüldüğünde `map` en çok içeren `cMap` öğeleri ve `pcMap` gerçekte yazılan cor_ıl_map değerlerin sayısını ayarlanır `map` dizisi.  
  
 IL haline getirilmiş dolmadığından veya eşleme bir profil oluşturucu tarafından sağlanan değildi, bu yöntemi döndürür `S_OK` ve ayarlar `pcMap` 0.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
