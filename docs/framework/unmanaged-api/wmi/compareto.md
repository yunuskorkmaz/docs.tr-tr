---
title: CompareTo işlevi (yönetilmeyen API Başvurusu)
description: CompareTo işlevi bir nesneyi başka bir WMI nesnesini karşılaştırır.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527622"
---
# <a name="compareto-function"></a>CompareTo işlevi
Başka bir Windows Yönetim nesnesi için bir nesne ile karşılaştırır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`flags`  
[in] Karşılaştırma için dikkate alınması gereken nesne özellikleri belirten bayraklar Bitsel bir birleşimi. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.

`pCompareTo`  

[in] Karşılaştırma için nesne. `pcompareTo` Geçerli bir olmalıdır [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örnek; olamaz `null`.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | İkinci çağrı `BeginEnumeration` bir çağrı göndermelisiniz olmadan yapılan [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Nesneler farklı. |
| `WBEM_S_SAME` | 0 | Nesneleri karşılaştırma bayraklarını tabanlı aynıdır. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) yöntemi.

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişken tanımlanmış *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda. Aşağıdaki bayraklar Bitsel bir birleşimi belirterek Karşılaştırmada dahil bireysel özelliklerini belirtebilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Kaynak (sunucu ve kaynaklarına ad alanı) yoksayın. |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1. | Tüm niteleyicileri yoksay (dahil olmak üzere **anahtarı** ve **dinamik**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Özelliklerin varsayılan değerlerini yoksayın. Bu bayrağı yalnızca sınıfları bir karşılaştırması için geçerlidir. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Niteleyici özelliği yoksayın. Bu bayrak hala niteleyicileri, dikkate ancak flavor farklılıklar yayma kuralları gibi yoksayar ve kısıtlamaları geçersiz kılar. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Dize değerleri karşılaştırma içinde çalışması yoksayar. Bu, hem dizeleri ve niteleyici değeri için geçerlidir. Özellik ve niteleyicisi adlarının karşılaştırma her zaman bu bayrağı ayarlanmış olduğundan bağımsız olarak büyük küçük harfe duyarlıdır. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Karşılaştırılan nesnelerin örneklerinin aynı sınıfın olduğunu varsayar. Sonuç olarak, bu bayrağı yalnızca örnekle ilgili bilgi karşılaştırır. Bu bayrak, performansı iyileştirmek için kullanın. Nesneleri aynı sınıfının emin değilseniz, sonuçlar tanımsızdır. |

Veya tek bir bileşik bayrağı şu şekilde belirtebilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Karşılaştırma içindeki tüm özelliklerini göz önünde bulundurun. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
