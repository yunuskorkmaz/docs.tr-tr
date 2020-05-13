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
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212236"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges Yöntemi
Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cbMetadata`  
 'ndaki Delta meta verilerinin bayt cinsinden boyutu.  
  
 `pbMetadata`  
 'ndaki Delta meta verilerini içeren arabellek. Arabelleğin adresi [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) yönteminden döndürülür.  
  
 Meta verilerdeki göreli sanal adresler (RVA) MSIL kodunun başlangıcına göre olmalıdır.  
  
 `cbIL`  
 'ndaki Delta MSIL kodunun bayt cinsinden boyutu.  
  
 `pbIL`  
 'ndaki Güncelleştirilmiş MSIL kodunu içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 `pbMetadata`Parametresi özel bir delta meta veri biçiminde ( [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)olarak çıktı olarak). `pbMetadata`önceki meta verileri temel olarak alır ve bu temele uygulanacak tek değişiklikleri açıklar.  
  
 Buna karşılık, `pbIL[` ] parametresi güncelleştirilmiş yöntemi için yenı MSIL içerir ve bu yöntem için ÖNCEKI MSIL 'i tamamen değiştirmek üzere tasarlanmıştır  
  
 Delta MSIL ve meta veriler hata ayıklayıcının belleğinde oluşturulduğunda, hata ayıklayıcı `ApplyChanges` değişiklikleri ortak dil çalışma zamanına (CLR) göndermek için çağırır. Çalışma zamanı, meta veri tablolarını güncelleştirir, yeni MSIL 'yi işleme koyar ve yeni MSIL 'nin tam zamanında (JıT) derlemesini ayarlar. Değişiklikler uygulandığında, hata ayıklayıcı sonraki Düzenle oturumuna hazırlanmak için [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) çağrısını çağırmalıdır. Hata ayıklayıcı daha sonra işleme devam edebilir.  
  
 Hata ayıklayıcı, `ApplyChanges` Delta meta verilerini içeren bir modüle her çağırdığında, değişiklikleri yaymak için kullanılan kopya hariç, Bu modülün meta verilerinin tüm kopyalarında aynı Delta meta verileriyle birlikte [ımetadatayayma:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) ' ı çağırmalıdır. Meta verilerin bir kopyası gerçek meta verilerle eşitlenmemiş hale gelirse, hata ayıklayıcı her zaman o kopyayı oluşturabilir ve yeni bir kopya alabilir.  
  
 `ApplyChanges`Yöntem başarısız olursa, hata ayıklama oturumu geçersiz bir durumdaydı ve yeniden başlatılması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
