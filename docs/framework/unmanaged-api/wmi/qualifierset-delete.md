---
title: QualifierSet_Delete işlevi (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174907"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete fonksiyonu
Belirtilen bir niteleyiciyi ada göre siler.  

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
[içinde] Bu parametre kullanılmaz.

`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.

`wszName`[içinde] Silinecek varamanın adı.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre `wszName` geçerli değil. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Bu elemeyi silerken yasa dışıdır. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen niteleyici bulunamadı. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Yerel geçersiz kılma silindi ve üst nesneden özgün niteleyici kapsam devam etti. |

## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemine bir çağrı yıkıyor.

Niteleyici yayılma kuralları nedeniyle, belirli bir niteleyici başka bir nesneden devralınmış ve yalnızca geçerli sınıf veya örnekte geçersiz kılınmış olabilir. Bu durumda, `QualifierSet_Delete` yöntem niteleyiciyi özgün devralınan değerine sıfırlar. Bu durumda işlev durum kodunu `WBEM_S_RESET_TO_DEFAULT`döndürür.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
