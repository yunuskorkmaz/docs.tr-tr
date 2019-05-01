---
title: ICorDebugModule2::ApplyChanges Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987975"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges Yöntemi
Meta veri değişiklikleri ve Microsoft Ara dil (MSIL) kodu değişiklikleri çalışan işlemi için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbMetadata`  
 [in] Delta meta verilerin bayt cinsinden boyutu.  
  
 `pbMetadata`  
 [in] Delta meta veriler içeren arabellek. Arabelleğin adresi döndürüldüğü [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) yöntemi.  
  
 Meta verilerde göreli sanal adreslerine (RVA) göre MSIL kodu başlangıcını olmalıdır.  
  
 `cbIL`  
 [in] MSIL kodu delta bayt cinsinden boyutu.  
  
 `pbIL`  
 [in] Güncelleştirilmiş MSIL kodu içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 `pbMetadata` Parametresi, bir özel delta meta veri biçiminde (tarafından çıkış [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` temel olarak önceki meta verileri alır ve bu Bankası'na uygulamak için tek tek değişiklikler açıklanmaktadır.  
  
 Buna karşılık, `pbIL[`] parametresi güncelleştirilmiş yöntemi için yeni MSIL içerir ve bu yöntem için önceki MSIL tamamen değiştirmek için tasarlanmıştır  
  
 Hata Ayıklayıcı'nın bellekte delta MSIL ve meta veriler oluşturulmuş hata ayıklayıcı çağırır `ApplyChanges` ortak dil çalışma zamanı (CLR) değişiklikleri göndermek için. Çalışma zamanı meta veri tablolarından güncelleştirmeleri, yeni MSIL işlemine yerleştirir ve yeni MSIL bir just-ın-time (JIT) derleme ayarlar. Hata ayıklayıcı, değişiklikler uygulandığında, çağırmalıdır [Imetadataemit2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) sonraki düzenleme oturumu için hazırlamak için. Hata ayıklayıcı, sonra işlemi devam edebilir.  
  
 Her hata ayıklayıcı çağırır `ApplyChanges` delta meta verileri olan bir modülde, aynı zamanda çağırmalıdır [Imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) tüm Bu modülün meta veri kopyalama dışında bulunan kopyalarını aynı delta meta verilerle değişiklikleri yaymak için kullanılır. Meta verilerinin bir kopyasını şekilde eşitleme dışı hale gelirse gerçek meta veriler ile hata ayıklayıcı her zaman hemen bu kopyayı atar ve yeni bir kopyasını alın.  
  
 Varsa `ApplyChanges` yöntem başarısız, hata ayıklama oturumu geçersiz bir durumda ve yeniden başlatılması gerekiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
