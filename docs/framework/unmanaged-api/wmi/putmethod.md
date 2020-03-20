---
title: PutMethod işlevi (Yönetilmeyen API Başvurusu)
description: PutMethod işlevi bir yöntem oluşturur.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174920"
---
# <a name="putmethod-function"></a>PutMethod fonksiyonu
Bir yöntem oluşturur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`wszName`  
[içinde] Oluşturulacak yöntemin adı.

`lFlags`  
[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`pSignatureIn`  
[içinde] Yöntem parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) `in` bir kopyasına işaretçi. Bu parametre ' olarak `null`ayarlanmışsa yoksayılır  

`pSignatureOut`  
[içinde]  Yöntem parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) `out` bir kopyasına işaretçi. Bu parametre ' olarak `null`ayarlanmışsa yoksayılır

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değildir. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Hem `[in, out]` *pInSignature* hem de *pOutSignature* nesnelerinde belirtilen yöntem parametresi farklı niteleyicilere sahiptir.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Bir yöntem parametresi **kimlik** niteleyicisinin belirtimini eksik. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Yöntem parametrelerine atanan kimlik serisi ardışık değildir veya 0'da başlamaz. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Bir yöntemin dönüş değerinin **bir kimlik** niteleyicisi vardır. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Bir üst sınıftan varolan bir yöntem adını yeniden kullanma girişiminde bulunuldu ve imzalar eşleşmedi. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bir çağrı yıkıyor.

Bu yöntem çağrısı yalnızca `ptr` CIM sınıf tanımı ise desteklenir. Yöntem işleme cim örneklerine işaret [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri kullanılamaz.

Kullanıcılar, alt puanla başlayan veya biten adlarla yöntem oluşturamaz. Bu sistem sınıfları ve özellikleri için ayrılmıştır.

Bir yöntem `in` için, `out` ve parametreler [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) nesnelerinde özellikler olarak tanımlanır.

Parametre, `[in/out]` her iki nesneye `pInSignature` de `pOutSignature` aynı özellik eklenerek tanımlanabilir. Bu durumda, özellikler aynı **kimlik** niteleyici değerini paylaşır.

[__Parameters](/windows/desktop/WmiSdk/--parameters) sınıf nesnesindeki `ReturnValue` her özelliğin, parametrelerin görüntülenme sırasını tanımlayan sıfır tabanlı sayısal bir değer olan **kimlik** niteleyicisi olması gerekir. İki parametre aynı **kimlik** değerine sahip olamaz ve **hiçbir kimlik** değeri atlanabilir. Her iki durum oluşursa, `PutMethod` işlev döndürür. `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`

## <a name="example"></a>Örnek

Örneğin, [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bakın.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
