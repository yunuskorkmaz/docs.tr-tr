---
title: BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginEnumeration işlevi bir numaralandırıcı numaralandırması başlangıcına sıfırlar.
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
ms.openlocfilehash: 9699f0cfc4e9fdb989337681b164cc1e703c1e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461266"
---
# <a name="beginenumeration-function"></a>BeginEnumeration işlevi
Bir numaralandırıcı geri numaralandırması başlangıç durumuna sıfırlar.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr` [in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`lEnumFlags`  
[in] Bayrakları veya açıklanan değerlerinin Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada bulunan özellikler denetimleri bölümü.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bayrakları birleşimi `lEnumFlags` geçersiz veya geçersiz bir bağımsız değişken belirtildi. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | İkinci çağrı `BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemi.

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.  Diğer bir gruptaki tüm bayrağıyla her grubundan bir bayrak birleştirebilirsiniz. Ancak, aynı gruptan bayrakları karşılıklı olarak birbirini dışlar. 

**Grup 1**

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtar oluşturan özellikleri içerir. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları özellikler içerir. |

**Grubu 2**

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Sistem özellikleri yalnızca numaralandırma sınırlayın. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yerel ve yayılan özellikler içerir, ancak Sistem özellikleri numaralandırma içinden çıkarın. |

Sınıflar için:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Sınıf tanımı'nda geçersiz kılınan özellikleri numaralandırma sınırlayın. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Geçerli sınıf tanımında geçersiz kılınan özellikleri ve yeni özellikleri sınıfında tanımlanan numaralandırma sınırlayın. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A karşı uygulamak için (yerine bir bayrak) maske bir `lEnumFlags` ya da denetlemek için değer `WBEM_FLAG_CLASS_OVERRIDES_ONLY` veya `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` ayarlanır. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Tanımlanan veya sınıfında değiştirilen özellikler numaralandırma sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Temel sınıflardan devralınır özellikler numaralandırma sınırlayın. |

İçin örnekleri:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Tanımlanan veya sınıfında değiştirilen özellikler numaralandırma sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Temel sınıflardan devralınır özellikler numaralandırma sınırlayın. |


## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
