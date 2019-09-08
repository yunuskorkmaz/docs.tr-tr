---
title: SpawnInstance işlevi (yönetilmeyen API Başvurusu)
description: SpawnInstance işlevi bir sınıfın yeni bir örneğini oluşturur.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529905bd9286520a8e09479bfc95ef0b614f53e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798212"
---
# <a name="spawninstance-function"></a>SpawnInstance işlevi
Bir sınıfın yeni bir örneğini oluşturur.    
  
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
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lFlags`  
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`ppNewInstance`  
dışı Sınıfın yeni örneğine işaretçiyi alır. Bir hata oluşursa, yeni bir nesne döndürülmez ve `ppNewInstance` değiştirilmemiş olarak kalır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`geçerli bir sınıf tanımı değil ve yeni örnekler üretilemedi. Tamamlanmamış ya da [Putclasswmı](putclasswmi.md)çağırarak Windows yönetimine kaydedilmemiş. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass``null`. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemine bir çağrı kaydırır.

`ptr`Windows yönetiminden alınmış bir sınıf tanımı olmalıdır. (Bir örnekten örnek oluşturma desteklendiğini, ancak döndürülen örnek boş olduğunu unutmayın.) Daha sonra bu sınıf tanımını yeni örnekler oluşturmak için kullanırsınız. Örneği Windows yönetimine yazmayı düşünüyorsanız [Putınstancewmi](putinstancewmi.md) işlevine yapılan bir çağrı gerekir.

`ppNewClass` Otomatik olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur. Bu davranışın üzerine yazılamıyor. Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için başka bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
