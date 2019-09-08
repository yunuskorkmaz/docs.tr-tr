---
title: BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi bir Numaralandırıcı numaralandırmanın başlangıcına sıfırlanır
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de36650aa2b206b5e9734b38c6067a3a79de610c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798785"
---
# <a name="beginenumeration-function"></a>BeginEnumeration işlevi
Bir numaralandırıcıyı numaralandırmanın başına geri döndürür.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lEnumFlags`\
'ndaki Numaralandırmada içerilen özellikleri denetleyen [açıklamalar](#remarks) bölümünde açıklanan bayrakların veya değerlerin bit düzeyinde birleşimi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | İçindeki `lEnumFlags` bayrakların birleşimi geçersiz ya da geçersiz bir bağımsız değişken belirtildi. |
|`WBEM_E_UNEXPECTED` | 0x8004101D | İçin bir araya giren `BeginEnumeration` [`EndEnumeration`](endenumeration.md)çağrı yapılmadan ikinci bir çağrı yapıldı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı kaydırır.

`lEnumFlags` Bağımsız değişken olarak geçirilebilecek bayraklar, *wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.  Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz. Ancak, aynı gruptaki Bayraklar birbirini dışlıyor. 

**1. Grup**

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarı oluşturan özellikleri ekleyin. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellikleri ekleyin. |

**Grup 2**

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Numaralandırmayı yalnızca sistem özellikleriyle sınırlayın. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yerel ve yayılmış özellikleri ekleyin, ancak Numaralandırmadaki sistem özelliklerini dışlayın. |

Sınıflar için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Sabit listesini, sınıf tanımında geçersiz kılınan özelliklerle sınırlayın. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Sabit listesini geçerli sınıf tanımında geçersiz kılınan özelliklerle ve sınıfta tanımlanan yeni özelliklerle sınırlayın. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Ya `lEnumFlags` da`WBEM_FLAG_CLASS_OVERRIDES_ONLY` ayarlanmış olup olmadığını denetlemek için bir değere karşı uygulanacak bir maske (bayrak yerine). `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın. |

Örnekler için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Sabit listesini, sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın. |

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
