---
description: 'Daha fazla bilgi edinin: IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi'
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
ms.openlocfilehash: 62d9ae73c216748cc8eb02aedd41cf19f475d071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800662"
---
# <a name="ixclrdataprocessgetruntimenamebyaddress-method"></a>IXCLRDataProcess:: GetRuntimeNameByAddress yöntemi

Verilen adres için bir ad alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

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
