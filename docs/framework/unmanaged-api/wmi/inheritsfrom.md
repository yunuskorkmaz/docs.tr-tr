---
title: DevralmalarFrom işlevi (Yönetilmeyen API Başvurusu)
description: InheritsFrom işlevi, bir sınıfın veya örneğin belirli bir üst sınıftan türediğini belirler.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174946"
---
# <a name="inheritsfrom-function"></a>DevralmalarFrom işlevi
Geçerli sınıfın veya örneğin belirli bir üst sınıftan türetilip türedip türetilemeyeceğini belirler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`wszAncestor`  
[içinde] Sınıfın adı. `wszAncestor`geçerli `LPCWSTR`bir işaret etmelidir.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Geçerli nesne `wszAncestor`devralır.  |
| `WBEM_S_FALSE` | 1 | Geçerli nesne ' den `wszAncestor`devralmaz. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor``null`. |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemine bir çağrı yıkıyor.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
