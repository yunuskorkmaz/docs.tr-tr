---
title: GetQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetQualifierSet işlevi, bir sınıf veya örnek için niteleyici kümesini alır.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 489e240af3f26e82f2459ac4b4dbd944639f78fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127447"
---
# <a name="getqualifierset-function"></a>GetQualifierSet işlevi
Bir sınıf örneği veya sınıf tanımı için niteleyici kümesini alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`ppQualSet`  
dışı Sınıf nesnesinin niteleyicilerine erişime izin veren arabirim işaretçisini alır. `ppQualSet` `null`olamaz. Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi değiştirilmemiş olarak kalır. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem yok. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre `null`. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) yöntemine bir çağrı kaydırır. 

[IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) , çağıranın bu niteleyicileri eklemesine, düzenlemesine veya silmesine izin verir. Bu tür eklenmiş, düzenlenmiş veya silinen niteleyiciler, tüm örnek veya sınıf tanımı için geçerlidir.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
