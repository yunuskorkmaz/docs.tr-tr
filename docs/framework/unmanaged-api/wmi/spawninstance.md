---
title: SpawnInstance işlevi (Yönetilmeyen API Başvurusu)
description: SpawnInstance işlevi sınıfın yeni bir örneğini oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176727"
---
# <a name="spawninstance-function"></a>SpawnInstance fonksiyonu
Sınıfın yeni bir örneğini oluşturur.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lFlags`  
[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`ppNewInstance`  
[çıkış] İşaretçiyi sınıfın yeni örneğine alır. Bir hata oluşursa, yeni bir nesne `ppNewInstance` döndürülür ve değiştirilmemiş bırakılır.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`geçerli bir sınıf tanımı değildir ve yeni örnekler doğuramaz. Ya eksik ya da [PutClassWmi](putclasswmi.md)çağırarak Windows Yönetimi kayıtlı olmamıştır. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass``null`. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemine bir çağrı yıklar.

`ptr`Windows Yönetimi'nden elde edilen bir sınıf tanımı olmalıdır. (Bir örnekten bir örnek yumurtlamanın desteklenir, ancak döndürülen örnek boş olduğunu unutmayın.) Daha sonra yeni örnekler oluşturmak için bu sınıf tanımını kullanırsınız. Örneği Windows Yönetimi'ne yazmak istiyorsanız [PutInstanceWmi](putinstancewmi.md) işlevine bir çağrı gereklidir.

Otomatik `ppNewClass` olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur. Bu davranış geçersiz kılınamaz. Alt sınıfların (türetilmiş sınıflar) oluşturulabileceği başka bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
