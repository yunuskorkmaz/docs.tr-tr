---
title: BeginMethodEnumeration fonksiyonu (Yönetilmeyen API Başvurusu)
description: BeginMethodEnumeration işlevi nesnenin yöntemlerinin numaralandırma başlar
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175050"
---
# <a name="beginmethodenumeration-function"></a>BeginMethodEnumeration işlevi
Nesne için kullanılabilir yöntemlerin numaralandırmasını başlatın.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lEnumFlags`  
[içinde] Tüm yöntemler için Sıfır (0) veya numaralandırmanın kapsamını belirten bir bayrak. Aşağıdaki bayraklar *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Numaralandırmayı sınıfın kendisinde tanımlanan yöntemlerle sınırlandırın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın. |

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`sıfır değildir ve belirtilen bayraklardan biri değildir. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) yöntemine bir çağrı yıkıyor.

Bu yöntem çağrısı yalnızca geçerli nesne bir sınıf tanımı ise desteklenir. Yöntem işleme örnekleri işaret [iWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri kullanılamaz. Yöntemleri numaralandırılan sıra, [IWbemClassObject'in](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)belirli bir örneği için değişmez olması garanti edilir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
