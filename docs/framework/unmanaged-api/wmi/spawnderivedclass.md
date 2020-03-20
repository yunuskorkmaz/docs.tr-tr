---
title: SpawnDerivedClass işlevi (Yönetilmeyen API Başvurusu)
description: SpawnDerivedClass işlevi bir nesneden türeyen yeni bir nesne oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174855"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass fonksiyonu
Belirtilen bir nesneden yeni türetilmiş bir sınıf nesnesi oluşturur.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lFlags`  
[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`ppNewClass`  
[çıkış] Yeni sınıf tanımı nesnesinin işaretçisini alır. Bir hata oluşursa, yeni bir nesne `ppNewClass` döndürülür ve değiştirilmemiş bırakılır. Değeri. `null`

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Bir örnekten bir sınıf yumurtlama gibi geçersiz bir işlem istendi. |
| `WBEM_E_INCOMPLETE_CLASS` | Kaynak sınıf windows yönetimi ile tam olarak tanımlanmadı veya kaydedilmedi, bu nedenle yeni bir türetilmiş sınıfa izin verilmez. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass``null`. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı yıkLar.

`ptr`oluşturulan nesnenin ana sınıfı haline gelen bir sınıf tanımı olmalıdır. Döndürülen nesne, geçerli nesnenin bir alt sınıfı olur.

Otomatik `ppNewClass` olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur. Bu davranış geçersiz kılınamaz. Alt sınıfların (türetilmiş sınıflar) oluşturulabileceği başka bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
