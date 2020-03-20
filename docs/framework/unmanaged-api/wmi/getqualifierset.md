---
title: GetQualifierSet fonksiyonu (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176779"
---
# <a name="getqualifierset-function"></a>GetQualifierSet fonksiyonu
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
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`ppQualSet`  
[çıkış] Sınıf nesnesinin niteleyicilerine erişim sağlayan arabirim işaretçisini alır. `ppQualSet`olamaz. `null` Bir hata oluşursa, yeni bir nesne döndürülür ve işaretçi değiştirilmemiş olarak bırakılır.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem yok. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre. `null` |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) yöntemine bir çağrı yıkıyor.

[IWbemQualifierSet işaretçisi,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) arayanın bu elemeleri eklemesini, düzenlemesini veya silmesini sağlar. Bu tür eklenen, düzenlenen veya silinen niteleyiciler tüm örnek veya sınıf tanımı için geçerlidir.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
