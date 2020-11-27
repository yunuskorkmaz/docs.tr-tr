---
title: 'IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi'
ms.date: 4/27/2020
api.name:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::GetRuntimeNameByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: tommcdon
ms.author: tommcdon
ms.openlocfilehash: 6648bdafe6e5cdd402bcfa02a148c57f0f1e209e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270493"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi

Verilen adres için bir ad alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetRuntimeNameByAddress(
    [in] CLRDATA_ADDRESS address,
    [in] ULONG32 flags,
    [in] ULONG32 bufLen,
    [out] ULONG32 *nameLen,
    [out, size_is(bufLen)] WCHAR nameBuf[],
    [out] CLRDATA_ADDRESS* displacement
);
```

## <a name="parameters"></a>Parametreler

`address`\
'ndaki `CLRDATA_ADDRESS` Bir kod adresini temsil eden bir değer.

`flags`\
'ndaki ' 0 ' olarak ayarlayın.

`bufLen`\
'ndaki Arabelleğin uzunluğu.

`namLen`\
dışı Döndürülen karakter sayısına yönelik bir işaretçi.

`namBuf`\
[Out, size_is ( `bufLen` )] `bufLen` çalışma zamanı adını depolayan uzunluğun giriş arabelleği.

`displacement`\
dışı `CLRDATA_ADDRESS` Döndürülen sembolün kod kaydırmasına yönelik bir işaretçi.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 16. yuvasına karşılık gelir.

> [!NOTE]
> Arabellek ad için yeterince büyük değilse, bu yöntem, `S_FALSE` gerekli arabellek uzunluğuna döndürür ve ayarlar `nameLen` .

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md)\
**Üst bilgi:** Seçim
**Kitaplık:** Seçim
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataProcess Arabirimi](ixclrdataprocess-interface.md)
