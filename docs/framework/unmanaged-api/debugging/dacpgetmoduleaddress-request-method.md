---
title: DacpGetModuleAddress::İstek Yöntemi
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179207"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::İstek Yöntemi

Yapıyı verilen çalışma zamanı yapısından doldurmak için bir istek gerçekleştirir.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>Parametreler

`pDataModule`\
[içinde] Tohum veri modülü için bir işaretçi.

## <a name="remarks"></a>Açıklamalar

Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz. Kullanmak için en kolay yolu uygulamayı taklit etmektir:

- `IXCLRDataModule*` Parametreüzerindeki `Request` yöntemi çağırarak elde edilen değeri aşağıdaki parametrelerle döndür`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Gereksinimler

**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üstbilgi:** Yok **Kütüphane:** Yok  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama](index.md)
- [DacpGetModuleAdres Arayüzü](dacpgetmoduleaddress-structure.md)
