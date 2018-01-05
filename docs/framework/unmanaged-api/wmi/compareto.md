---
title: "CompareTo işlevi (yönetilmeyen API Başvurusu)"
description: "CompareTo işlevi başka bir WMI nesnesi bir nesneyi karşılaştırır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 038074b5bb3adc816caa226d3167395758d2ae57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="compareto-function"></a>CompareTo işlevi
Nesneyi başka bir Windows Yönetim nesnesi için karşılaştırır.  

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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`flags`  
[in] Karşılaştırma için dikkate alınması gereken nesne özellikleri belirten bayrakları Bitsel bir birleşimi. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.

`pCompareTo`  

[in] Karşılaştırma için nesnesi. `pcompareTo`Geçerli bir olmalıdır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örnek; olamaz `null`.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | İkinci çağrı `BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `EndEnumeration` ](endenumeration.md). |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
| `WBEM_S_DIFFERENT` | 0x40003 | Nesneleri farklıdır. |
| `WBEM_S_SAME` | 0 | Nesneleri karşılaştırma bayrakları dayalı aynıdır. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) yöntemi.

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda. Aşağıdaki bayraklar Bitsel bir birleşimi belirterek Karşılaştırmada söz konusu tek tek özellikleri belirtebilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | Kaynak (sunucu ve bunların nereden geldiğini ad alanı) yoksay. |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1. | Tüm niteleyicileri yoksay (de dahil olmak üzere **anahtar** ve **dinamik**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | Özelliklerin varsayılan değerleri yok sayın. Bu bayrak, yalnızca sınıfları bir karşılaştırması için geçerlidir. |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | Niteleyici özellikleri yoksay. Bu bayrak hala niteleyicileri, dikkate alır, ancak özellik farklılıklar yayma kurallar gibi yoksayar ve kısıtlamalarını geçersiz kılmak. |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | Dize değerleri karşılaştırma içinde durumu yoksay. Bu, hem dizeler ve niteleyicisi değerleri için geçerlidir. Özellik ve niteleyicisi adları karşılaştırması bu bayrağı ayarlanmış olduğundan bağımsız olarak her zaman duyarlıdır. |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | Karşılaştırılan nesnelerin aynı sınıf örneklerinin olduğunu varsayar. Sonuç olarak, bu bayrak örneği ile ilgili bilgiler yalnızca karşılaştırır. Bu bayrak, performansı iyileştirmek için kullanın. Nesneleri aynı sınıfının emin değilseniz, sonuçları tanımlanmamış. |

Veya tek bir birleşik bayrak aşağıdaki gibi belirtin:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | Karşılaştırma tüm özelliklerini göz önünde bulundurun. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
