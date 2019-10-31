---
title: PutClassWmi işlevi (yönetilmeyen API Başvurusu)
description: PutClassWmi işlevi yeni bir sınıf oluşturur veya var olan bir sınıfı güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101786"
---
# <a name="putclasswmi-function"></a>PutClassWmi işlevi

Yeni bir sınıf oluşturur veya var olan bir sınıfı güncelleştirir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametreler

`pObject`\
'ndaki Geçerli bir sınıf tanımına yönelik işaretçi. Tüm gerekli özellik değerleriyle doğru başlatılmış olmalıdır.

`lFlags`\
'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlanırsa, WMI değişiklik yapılan Flavor ile hiçbir niteleyicileri depolamaz. <br> Ayarlanmamışsa, bu nesnenin yerelleştirilmemiş olduğu varsayılır ve tüm niteleyiciler bu örnekle birlikte depolanır. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Yoksa sınıfı oluşturun veya zaten varsa üzerine yazın. |
| `WBEM_FLAG_UPDATE_ONLY` | 1\. | Sınıfını güncelleştirin. Çağrının başarılı olması için sınıfın mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Sınıfı oluşturun. Sınıf zaten mevcutsa çağrı başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrak, yarı zaman uyumlu bir çağrıya neden olur. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Bu sınıfın değiştiğini göstermek için, push sağlayıcıları `PutClassWmi` çağırırken bu bayrağı belirtmesi gerekir. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Türetilmiş sınıf yoksa ve bu sınıfın örneği yoksa bir sınıfın güncelleştirilmesini sağlar. Ayrıca değişiklik, açıklama niteleyicisi gibi önemli niteleyicilere ise tüm durumlarda güncelleştirmelere izin verir. Sınıfın örnekleri veya değişiklikleri önemli niteleyicilere sahipse güncelleştirme başarısız olur. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Değişiklik alt sınıflarla çakışmaya neden olmadığı sürece alt sınıflar olsa bile sınıfların güncelleştirmelerine izin verir. Örneğin, bu bayrak, alt sınıfların hiçbirinde daha önce bahsedilen temel sınıfa yeni bir özelliğin eklenmesine izin verir. Sınıfta örnek varsa, güncelleştirme başarısız olur. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | çakışan alt sınıflar varsa sınıfların güncelleştirmelerini zorlar. Örneğin, bu bayrak bir alt sınıfta bir sınıf niteleyicisi tanımlanmışsa bir güncelleştirmeyi zorlar ve temel sınıf var olan aynı niteleyiciyi eklemeye çalışır. Zorlama modunda, alt sınıfta çakışan niteleyiciyi silerek TIS çakışması çözümlenir. |

`pCtx`\
'ndaki Genellikle, bu değer `null`. Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.

`ppCallResult`\
dışı `null`, bu parametre kullanılmaz. `lFlags` `WBEM_FLAG_RETURN_IMMEDIATELY`içeriyorsa, işlev hemen `WBEM_S_NO_ERROR`ile döndürür. `ppCallResult` parametresi, yeni bir [ıwbemcallresult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesnesine bir işaretçi alır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının sınıfları oluşturma veya değiştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Belirtilen sınıf geçerli değil. Genellikle, `pObject` bir örnek nesnesini belirtir. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Belirtilen sınıf adı geçerli değil. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Bir alt sınıfı geçersiz kılacak bir değişiklik yapmak için girişimde bulunuldu. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` bayrağı belirtildi, ancak sınıf zaten var. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` `lFlags`belirtildi ve sınıf bulunamadı. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Sınıflar için gereken özellikler hepsi ayarlanmamış. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor. [Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemServices::P utClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) yöntemine yapılan çağrıyı sarmalanmış.

Kullanıcı, bir alt çizgi karakteriyle başlayan veya biten adlara sahip sınıflar oluşturmayabilir.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
