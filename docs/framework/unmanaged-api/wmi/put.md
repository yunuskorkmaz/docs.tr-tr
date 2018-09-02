---
title: Put işlevi (yönetilmeyen API Başvurusu)
description: Put işlevi, adlandırılmış bir özelliği için yeni bir değer atar.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43460991"
---
# <a name="put-function"></a>Put işlevi
Adlandırılmış bir özelliği, yeni değere ayarlar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`wszName`  
[in] Özelliğin adı. Bu parametre olamaz `null`.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pVal`   
[in] Geçerli bir işaretçi `VARIANT` , yeni özellik değeri olur. Varsa `pVal` olan `null` veya işaret eden bir `VARIANT` türü `VT_NULL`, özelliği `null`. 

`vtType`  
[in] Türünü `VARIANT` işaret ettiği `pVal`. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.
 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Özellik türü tanınmıyor. Bu değer, sınıf zaten varsa, sınıf örnekleri oluşturulurken döndürülür. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | İçin örnek: gösterir `pVal` işaret eden bir `VARIANT` özelliği için yanlış türde. <br/> Sınıf tanımları için: özellik üst sınıfta zaten mevcut ve yeni bir COM tür eski bir COM türünden farklıdır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.

Bu işlev her zaman geçerli özellik değeri ile yeni bir üzerine yazar. Varsa [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaret eden bir sınıf tanımı için `Put` oluşturur veya özellik değerini güncelleştirir. Zaman [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaret eden bir CIM örneğine `Put` özellik değeri yalnızca; güncelleştirir `Put` bir özellik değeri oluşturulamıyor.

`__CLASS` Sistem özelliği olduğunda yalnızca yazılabilir sınıfı oluşturma sırasında boş bırakılamaz. Diğer tüm sistem özellikleri salt okunurdur.

Kullanıcı özellikleri ile başlayamaz veya bitemez bir alt çizgi ("_") adları oluşturulamıyor. Bu, sistem sınıfları ve özellikleri için ayrılmıştır.

Özelliği ayarlarsanız `Put` üst sınıfta exists işlevi, özelliğinin varsayılan değeri üst sınıfı türü Özellik türüyle eşleşmiyor sürece değiştirilir. Özelliği yok ve tür uyuşmazlığı değil, ceated özelliğidir.

Kullanım `vtType` yalnızca bir CIM sınıf tanımına yeni özellikler oluştururken, parametre ve `pVal` olduğu `null` veya işaret bir `VARIANT` türü `VT_NULL`. Bu durumda, `vType` parametresi, özelliğin CIM türü belirtir. Diğer her durumda `vtType` 0 olmalıdır. `vtType` temel alınan nesne örneği ise 0 olmalıdır (bile `Val` olan `null`) özelliğinin türü sabittir ve değiştirilemez.   

## <a name="example"></a>Örnek

Bir örnek için bkz. [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
