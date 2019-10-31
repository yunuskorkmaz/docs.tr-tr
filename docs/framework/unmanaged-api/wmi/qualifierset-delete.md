---
title: QualifierSet_Delete işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Delete işlevi bir niteleyiciyi ada göre siler.
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
ms.openlocfilehash: e7bedcb5c56f9976f8dfd2619081971075d0d809
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127296"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete işlevi
Belirtilen niteleyiciyi ada göre siler.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`   
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`wszName`   
'ndaki Silinecek niteleyicinin adı.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` parametresi geçerli değil. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Bu niteleyiciyi silme geçersizdir. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen niteleyici bulunamadı. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Yerel geçersiz kılma silindi ve üst nesneden gelen özgün niteleyici kapsamı sürdürüyor. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet::D Sil](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemine bir çağrı kaydırır.

Niteleyici yayma kuralları nedeniyle, belirli bir niteleyici başka bir nesneden devralınmış olabilir ve yalnızca geçerli sınıfta veya örnekte geçersiz kılınır. Bu durumda `QualifierSet_Delete` yöntemi, niteleyiciyi özgün devralınmış değerine sıfırlar. Bu durumda işlev `WBEM_S_RESET_TO_DEFAULT`durum kodunu döndürür.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
