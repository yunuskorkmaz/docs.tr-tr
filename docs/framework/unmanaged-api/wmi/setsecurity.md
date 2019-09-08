---
title: SetSecurity işlevi (yönetilmeyen API Başvurusu)
description: SetSecurity işlevi, geçerli iş parçacığının kimliğe bürünme belirtecini alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798243"
---
# <a name="setsecurity-function"></a>SetSecurity işlevi

Geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecini alır. 

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
dışı İşlev döndürüldüğünde, belirtecin [resetsecurity](resetsecurity.md) işlevini çağırarak sıfırlanmasının `boolean` gerekip gerekmediğini belirten bir işaretçi içerir.

`token`\
dışı İşlev döndürüldüğünde, geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecinin tanıtıcısına yönelik bir işaretçi içerir. Geçerli iş parçacığıyla ilişkili `null` bir belirteç yoksa değeri bu olabilir. 

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri (0) `S_OK` olur.

İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.

## <a name="requirements"></a>Gereksinimler

 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi** WMINet_Utils. IDL

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
