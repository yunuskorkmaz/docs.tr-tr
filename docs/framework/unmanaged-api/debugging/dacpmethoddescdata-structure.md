---
title: DacpMethodDescData Yapısı
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203203"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData Yapısı

Bir yöntemin çalışma zamanı bilgileri için transport arabellek tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>Üyeler

| Üye                       | Açıklama                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Çalışma zamanı yerel kod yöntemin belirli örneklemesi için kullanılabilir olup olmadığını gösterir. |
| `bIsDynamic`                 | Basit kod oluşturma yöntemini dinamik olarak oluşturulur, gösterir.           |
| `wSlotNumber`                | Yöntem tablosunu yöntemin yuva numarası.                                                   |
| `NativeCodeAddr`             | Yöntemin ilk yerel adres.                                                            |
| `data`                       | Çalışma zamanı tarafından dahili olarak kullanılan arabellek için işaretçi.                                             |
| `MethodDescPtr`              | İşaretçi `MethodDesc` çalışma zamanında.                                                     |
| `nativeCodeInfo`             | Dahili yöntemleri izlemek için çalışma zamanı tarafından kullanılan arabellek için işaretçi.                            |
| `moduleInfo`                 | Çalışma zamanı tarafından modülü bilgileri için dahili olarak kullanılan arabellek için işaretçi.                      |
| `MDToken`                    | Belirtilen yöntemle ilişkili belirteci.                                                         |
| `payloadGC`                  | Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabellek için işaretçi.                          |
| `payloadGC2`                 | Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabellek için işaretçi.                          |
| `managedDynamicMethodObject` | Yöntem dinamik ise, çalışma zamanı bu arabellek izleme bilgileri için dahili olarak kullanır.     |
| `requestedIP`                | Yerel kod adresi verildiğinde istek başına yapısı doldurmak için kullanılır.                    |
| `rejitDataCurrent`           | Yöntemin belgelenmiş en son sürüm hakkında bilgi.                                   |
| `rejitDataRequested`         | İstenen yerel adres için Rejit bilgileri.                                             |
| `cJittedRejitVersions`       | İzleme aracılığıyla rejitted yöntemi çağrıldıysa sayısı.                           |

## <a name="remarks"></a>Açıklamalar

Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez. Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** None  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ortak Veri Türleri](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
