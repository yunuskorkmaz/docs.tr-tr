---
title: SetSecurity işlevi (Yönetilmeyen API Başvurusu)
description: SetSecurity işlevi geçerli iş parçacığının kimliğe bürünme belirteci alır.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176740"
---
# <a name="setsecurity-function"></a>SetSecurity işlevi

Geçerli iş parçacığı ile ilişkili kimliğe bürünme belirteci alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a>Parametreler

`pNeedToReset`\
[çıkış] İşlev döndüğünde, [ResetSecurity](resetsecurity.md) `boolean` işlevini çağırarak belirteç sıfırlanıp sıfırlanmayacağını belirten bir işaretçi içerir.

`token`\
[çıkış] İşlev döndüğünde, geçerli iş parçacığı ile ilişkili kimliğe bürünme belirteci işparçacığı için bir işaretçi içerir. Geçerli iş `null` parçacığı ile ilişkili bir belirteç varsa değeri olabilir.

## <a name="return-value"></a>Döndürülen değer

İşlev başarılı olursa, iade `S_OK` değeri (0) olur.

İşlev başarısız olursa, iade değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini arayın.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).

 **Üstbilgi:** WMINet_Utils.idl

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
