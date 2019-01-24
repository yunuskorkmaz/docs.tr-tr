---
title: InheritsFrom işlevi (yönetilmeyen API Başvurusu)
description: InheritsFrom işlevi bir sınıf veya örnek belirli üst sınıftan türetilen olup olmadığını belirler.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078950b4e46ea587c2f39986963ec129f4ec1f1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618389"
---
# <a name="inheritsfrom-function"></a>InheritsFrom işlevi
Geçerli sınıf veya örnek belirtilen üst sınıftan türetilen olup olmadığını belirler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`wszAncestor`  
[in] Sınıf adı. `wszAncestor` Geçerli bir işaret etmelidir `LPCWSTR`.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Geçerli nesnenin miras `wszAncestor`.  |
| `WBEM_S_FALSE` | 1. | Geçerli nesne öğesinden devralmayan `wszAncestor`. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` olan `null`. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
