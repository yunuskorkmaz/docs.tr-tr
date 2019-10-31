---
title: BeginMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginMethodEnumeration işlevi, nesne yöntemlerinin bir listesini başlatır
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
ms.openlocfilehash: a27787052757098d4edb2d8516e22d8a03b7009a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138784"
---
# <a name="beginenumeration-function"></a>BeginEnumeration işlevi
Nesne için kullanılabilen yöntemlerin bir listesini başlatır.  

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
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lEnumFlags`  
'ndaki Tüm yöntemler için sıfır (0) veya numaralandırmanın kapsamını belirten bir bayrak. Aşağıdaki bayraklar, *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Sabit listesini sınıfta tanımlanan yöntemlerle sınırlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın. |

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags` sıfır değil ve belirtilen bayraklardan biri değil. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) yöntemine bir çağrı kaydırır.

Bu yöntem çağrısı yalnızca geçerli nesne bir sınıf tanımı ise desteklenir. Yöntem işleme, örnekleri işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçilerinden kullanılamıyor. Yöntemlerin numaralandırıldıkları sıranın belirli bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)örneği için sabit olması garanti edilir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
