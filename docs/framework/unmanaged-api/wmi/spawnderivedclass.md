---
title: SpawnDerivedClass işlevi (yönetilmeyen API Başvurusu)
description: SpawnDerivedClass işlevi, bir nesneden türetilen yeni bir nesne oluşturur.
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
ms.openlocfilehash: 8020dd851b6773e6c76c53892c4b2bc21e4261bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716518"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass işlevi

Belirtilen nesneden yeni türetilmiş sınıf nesnesi oluşturur.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lFlags`  
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`ppNewClass`  
dışı Yeni sınıf tanımı nesnesine yönelik işaretçiyi alır. Bir hata oluşursa, yeni bir nesne döndürülmez ve `ppNewClass` değiştirilmemiş olarak kalır. Değeri olamaz `null` .

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Örnekten bir sınıfı oluşturmak gibi geçersiz bir işlem istendi. |
| `WBEM_E_INCOMPLETE_CLASS` | Kaynak sınıf tamamen tanımlanmamış veya Windows yönetimine kaydolmadı, bu nedenle yeni bir türetilmiş sınıfa izin verilmez. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`, `null` değeridir. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı kaydırır.

`ptr` oluşturulan nesnenin üst sınıfı haline gelen bir sınıf tanımı olmalıdır. Döndürülen nesne geçerli nesnenin bir alt sınıfı olur.

Otomatik olarak döndürülen yeni nesne, `ppNewClass` geçerli nesnenin bir alt sınıfı olur. Bu davranışın üzerine yazılamıyor. Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için başka bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
