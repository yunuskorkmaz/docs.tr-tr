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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860811"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData Yapısı

Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
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
| `bHasNativeCode`             | Çalışma zamanının, yöntemin belirli bir örneği için kullanılabilir yerel koda sahip olup olmadığını gösterir. |
| `bIsDynamic`                 | Yöntemin hafif kod üretimi aracılığıyla dinamik olarak oluşturulup oluşturulmayacağını gösterir.           |
| `wSlotNumber`                | Yöntem tablosundaki yuva numarası.                                                   |
| `NativeCodeAddr`             | Metodun ilk yerel adresi.                                                            |
| `data`                       | Çalışma zamanı tarafından dahili olarak kullanılan arabelleğin işaretçisi.                                             |
| `MethodDescPtr`              | Çalışma zamanında öğesine `MethodDesc` işaretçisi.                                                     |
| `nativeCodeInfo`             | Yöntemleri izlemek için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.                            |
| `moduleInfo`                 | Modül bilgileri için çalışma zamanı tarafından dahili olarak kullanılan bir arabelleğin işaretçisi.                      |
| `MDToken`                    | Verilen yöntemle ilişkili belirteç.                                                         |
| `payloadGC`                  | Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.                          |
| `payloadGC2`                 | Çalışma zamanı tarafından dahili olarak kullanılan bir çöp toplama arabelleğinin işaretçisi.                          |
| `managedDynamicMethodObject` | Yöntem dinamik ise, çalışma zamanı bu arabelleği bilgi izleme için dahili olarak kullanır.     |
| `requestedIP`                | Yerel kod adresi verildiğinde istek başına yapıyı doldurmak için kullanılır.                    |
| `rejitDataCurrent`           | Metodun en son belgelenmiş sürümü hakkında bilgi.                                   |
| `rejitDataRequested`         | İstenen yerel adres için ReJIT bilgileri.                                             |
| `cJittedRejitVersions`       | Metodun izleme aracılığıyla yeniden derlenen sayısı.                           |

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Ortak Veri Türleri](../common-data-types-unmanaged-api-reference.md)
