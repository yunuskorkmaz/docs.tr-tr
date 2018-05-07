---
title: QualifierSet_Put işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Put işlevi adlandırılmış niteleyici ve değerini yazar.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ccb0aef0e998ffccd7526f9f0554bceb892001b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put işlevi
Değeri ve adlandırılmış niteleyicisi yazar. Yeni niteleyici aynı ada sahip önceki değerin üzerine yazar. Niteleyici mevcut değilse oluşturulur. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmıyor.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.

`wszName`   
[in] Yazılacak Niteleyici adı.

`pVal` [in] Geçerli bir işaretçi `VARIANT` niteleyicisi yazmak için içerir. Bu parametre olamaz `null`.

`lFlavor` [in] Bu Niteleyici için istenen niteleyici özellikleri tanımlar sabitlerden biri. Varsayılan değer `WBEM_FLAVOR_OVERRIDABLE` (0).

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Bir türetilmiş sınıf veya örnek niteleyici geçersiz kılınabilir. **Varsayılan değer budur.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1. | Niteleyici örneklerine yayılır. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Niteleyici için türetilen sınıflar yayılır. |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | Niteleyici bir türetilmiş sınıf veya örnek değiştirilemiyor. |
| ' WBEM_FLAVOR_AMENDED | 0x80 | Niteleyici yerelleştirilmiştir. |

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Belirtmek için geçersiz bir deneme vardı **anahtar** niteleyici bir özellikte bir anahtar olamaz. Anahtarları belirtilen om c; bir nesne için ass tanımı ve örnek bazında değiştirilemez. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametresi geçerli niteleyici türü değil. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Çağrı mümkün değildir `QualifierSet_Put` sahip olan nesne izin vermiyor çünkü niteleyici yöntemini geçersiz kılar. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
