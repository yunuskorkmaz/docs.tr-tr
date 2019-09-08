---
title: Putınstancewmi işlevi (yönetilmeyen API Başvurusu)
description: Putınstancewmi işlevi, var olan bir sınıfın örneğini oluşturur veya güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798377"
---
# <a name="putinstancewmi-function"></a>Putınstancewmi işlevi

Var olan bir sınıfın örneğini oluşturur veya güncelleştirir. Örnek, WMI deposuna yazılır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametreler

`pInst`\
'ndaki Yazılacak örneğe yönelik bir işaretçi.

`lFlags`\
'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlanırsa **, WMI değişiklik yapılan Flavor ile** hiçbir niteleyicileri depolamaz. <br> Ayarlanmamışsa, bu nesnenin yerelleştirilmemiş olduğu varsayılır ve tüm niteleyiciler bu örnekle birlikte depolanır. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Yoksa örneği oluşturun veya zaten varsa üzerine yazın. |
| `WBEM_FLAG_UPDATE_ONLY` | 1\. | Örneği güncelleştirin. Çağrının başarılı olması için örneğin mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Örneği oluşturun. Örnek zaten mevcutsa çağrı başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrak, yarı zaman uyumlu bir çağrıya neden olur. |

`pCtx`\
'ndaki Genellikle, bu değer `null`. Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.

`ppCallResult`\
dışı Varsa `null`, bu parametre kullanılmaz. İçeriyorsa, işlev hemen ile `WBEM_S_NO_ERROR`döner. `WBEM_FLAG_RETURN_IMMEDIATELY` `lFlags` Parametresi `ppCallResult` , yeni bir [ıwbemcallresult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesnesine bir işaretçi alır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının belirtilen sınıfın bir örneğini güncelleştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Bu örneği destekleyen sınıf geçerli değil. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | bir `null` **dizinli** veya **Not_Null** niteleyicisi tarafından işaretlenen bir özellik `null`için bir belirtildi. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Belirtilen örnek geçerli değil. (Örneğin, bir sınıfla `PutInstanceWmi` çağırmak bu değeri döndürür.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Bayrak belirtildi, ancak örnek zaten var. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`' de `lFlags`belirtildi, ancak örnek yok. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor. [Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemServices::P Utınstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) yöntemine bir çağrı kaydırır.

`PutInstanceWmi` İşlevi örnek oluşturmayı ve yalnızca varolan sınıfların örneklerini güncelleştirmeyi destekler.  `pCtx` Parametresinin nasıl ayarlandığına bağlı olarak, örneğin özelliklerinin bazıları veya tümü güncellenir.

Tarafından `pInst` işaret edilen örnek bir alt sınıfa ait olduğunda, Windows yönetimi, alt sınıfın türetildiği sınıflardan sorumlu tüm sağlayıcıları çağırır. Özgün `PutInstanceWmi` isteğin başarılı olması için bu sağlayıcıların tümünün başarılı olması gerekir. Hiyerarşide en üstteki sınıfı destekleyen sağlayıcı ilk olarak çağırılır. Çağırma sırası en üstteki sınıfın alt sınıfıyla devam eder ve Windows yönetimi, tarafından `pInst`işaret edilen örneğe sahip olan sınıfa ait sağlayıcıya ulaşana kadar üstten alta doğru ilerler.
Windows yönetimi, bir örneğin alt sınıflarının herhangi biri için sağlayıcıları çağırmaz.

Bir uygulamanın bir sınıf hiyerarşisine ait bir örneği güncelleştirmesi gerektiğinde, `pInst` parametresinin değiştirilecek özellikleri içeren örneğe işaret olması gerekir. Diğer bir deyişle, **ClassB**'ye ait bir hedef örneği göz önünde bulundurun. **ClassB** örneği **ClassA**'Dan türetilir ve **ClassA** , **Propa**özelliğini tanımlar. Bir uygulama **ClassB** örneğinde **Propa** değerinde bir değişiklik yapmak istiyorsa, bu örnek bir **ClassA**örneği yerine bu örneğe ayarlanmalıdır `pInst` .

Soyut `PutInstanceWmi` sınıfın bir örneğine çağrı yapılmasına izin verilmez.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
