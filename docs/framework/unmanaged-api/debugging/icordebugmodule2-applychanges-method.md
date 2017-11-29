---
title: "ICorDebugModule2::ApplyChanges Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.ApplyChanges
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51c14bd6937d4b588227f7cf748c9a8052fb449c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges Yöntemi
Meta veri değişiklikleri ve Microsoft Ara dili (MSIL) kod değişiklikleri çalışan işlemi için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cbMetadata`  
 [in] Delta meta verilerin bayt cinsinden boyutu.  
  
 `pbMetadata`  
 [in] Delta meta veriler içeren bir arabellek. Arabellek adres alanından döndürülür [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) yöntemi.  
  
 Meta verilerde göreli sanal adresleri (RVAs) MSIL kod başlangıç göreli olmalıdır.  
  
 `cbIL`  
 [in] MSIL kod delta bayt cinsinden boyutu.  
  
 `pbIL`  
 [in] Güncelleştirilmiş MSIL kodu içeren bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 `pbMetadata` Parametredir özel delta meta veri biçiminde (tarafından çıkış [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata`temel olarak önceki meta verileri alır ve bu Bankası'na uygulamak için ayrı ayrı değişiklikleri açıklar.  
  
 Buna karşılık, `pbIL[`] parametresi güncelleştirilmiş yöntemi için yeni MSIL içerir ve bu yöntem için önceki MSIL tamamen değiştirmek için tasarlanmıştır  
  
 Hata Ayıklayıcı'nın bellekte delta MSIL ve meta veri oluşturulduğunda, hata ayıklayıcı çağırır `ApplyChanges` ortak dil çalışma zamanı (CLR) değişiklikleri göndermek için. Çalışma zamanı meta veri tablolarından güncelleştirir, yeni MSIL işlemine yerleştirir ve yeni MSIL bir tam zamanında (JIT) derleme ayarlar. Değişikliklerin uygulanması, hata ayıklayıcı çağırmalıdır [Imetadataemit2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) sonraki düzenleme oturumu için hazırlamak için. Hata ayıklayıcı, sonra işlemi devam edebilir.  
  
 Hata ayıklayıcıyı zaman çağırır `ApplyChanges` delta meta veri olan bir modül üzerinde bu da çağırmalıdır [Imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) tüm Bu modülün meta kopyalama dışında kendi kopyalarını aynı delta meta verilerle değişiklikleri yaymak üzere kullanılır. Meta verilerinin bir kopyasını şekilde eşitleme hale gelirse gerçek meta verileriyle hata ayıklayıcı her zaman hemen bu kopyayı throw ve yeni bir kopyasını edinin.  
  
 Varsa `ApplyChanges` yöntem başarısız, hata ayıklama oturumu geçersiz bir durumda ve yeniden başlatılması gerekiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
