---
title: QualifierSet_Delete işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Delete işlev adına göre bir niteleyici siler.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 543cc63b3e2188c11a6a8bf1eaa846461375be99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180082"
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete işlevi
Belirtilen bir niteleyici adıyla siler.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.

`wszName`   
[in] Silinecek niteleyicisi adı.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` Parametresi geçerli değil. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Bu niteleyici silme geçersizdir. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen niteleyicisi nebyl nalezen. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Yerel geçersiz kılma silindi ve özgün niteleyici üst nesneden kapsam devam ediyor. |

## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemi.

Niteleyici yayma kuralları nedeniyle, belirli bir niteleyici alınan başka bir nesneden ve yalnızca geçerli sınıf veya örnek içinde geçersiz kılındı. Bu durumda, `QualifierSet_Delete` yöntemi niteleyici özgün devralınan değerine sıfırlar. İşlev bu durumda, durum kodu döndürür `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
