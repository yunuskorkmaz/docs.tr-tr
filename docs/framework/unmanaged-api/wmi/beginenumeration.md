---
title: Başlama fonksiyonu (Yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi numaralandırmanın başlangıcına kadar bir numaralandırıcıyı sıfırlar
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176883"
---
# <a name="beginenumeration-function"></a>BeginEnumeration işlevi
Numaralandırmanın başına kadar bir numaralandırıcıyı sıfırlar.  

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
[içinde] Bu parametre kullanılmaz.

`ptr`\
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lEnumFlags`\
[içinde] [Numaralandırmada](#remarks) yer alan özellikleri denetleyen Açıklamalar bölümünde açıklanan bayrakların veya değerlerin bityişli bir birleşimi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bulunan bayrakların `lEnumFlags` birleşimi geçersiz veya geçersiz bir bağımsız değişken belirtilmiş. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | İkinci bir `BeginEnumeration` arama, müdahale etmeden [`EndEnumeration`](endenumeration.md)yapıldı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırmabaşlatmak için yeterli bellek kullanılabilir değil. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı yıkıyor.

`lEnumFlags` Bağımsız değişken *WbemCli.h* üstbilgi dosyasında tanımlandığı şekilde geçirilebilen bayraklar veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.  Her gruptan bir bayrağı başka bir gruptan herhangi bir bayrakla birleştirebilirsiniz. Ancak, aynı grubun bayrakları birbirini dışlar.

**Grup 1**

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarı oluşturan özellikleri ekleyin. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellikleri ekleyin. |

**Grup 2**

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Numaralandırmayı yalnızca sistem özellikleriyle sınırlandırın. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yerel ve yayılan özellikleri ekleyin, ancak sistem özelliklerini numaralandırmadan hariç tutar. |

Sınıflar için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Numaralandırmayı sınıf tanımında geçersiz kılınan özelliklerle sınırlandırın. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Numaralandırmayı geçerli sınıf tanımında geçersiz kılınan özelliklerle ve sınıfta tanımlanan yeni özelliklerle sınırlandırın. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Bir maske (bayrak yerine) bir `lEnumFlags` değer karşı ya `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` da ayarlanmış olup olmadığını kontrol etmek için uygulamak için. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Numaralandırmayı sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlandırın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın. |

Örneğin:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Numaralandırmayı sınıfın kendisinde tanımlanan veya değiştirilen özelliklerle sınırlandırın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
