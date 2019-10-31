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
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120220"
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
dışı İşlev döndürüldüğünde, belirtecin [Resetsecurity](resetsecurity.md) işlevini çağırarak sıfırlanması gerekip gerekmediğini belirten `boolean` bir işaretçi içerir.

`token`\
dışı İşlev döndürüldüğünde, geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecinin tanıtıcısına yönelik bir işaretçi içerir. Geçerli iş parçacığıyla ilişkili bir belirteç yoksa, değeri `null` olabilir. 

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** WMINet_Utils. IDL

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
