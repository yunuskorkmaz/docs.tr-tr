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
ms.openlocfilehash: 7200e3a19fcadabb5e149c38b620b3f60907c392
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948546"
---
# <a name="setsecurity-function"></a>SetSecurity işlevi

Geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini alır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>Parametreler

`pNeedToReset`\
[out] İşlevi döndüğünde, bir işaretçi içeren bir `boolean` belirten belirteç çağırarak sıfırlama olmadığını [ResetSecurity](resetsecurity.md) işlevi.

`token`\
[out] İşlevi döndüğünde, geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini işlemek için bir işaretçi içerir. Değeri olabilir `null` geçerli iş parçacığıyla ilişkilendirilmiş hiçbir belirteç olup olmadığını. 

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur. Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** WMINet_Utils.idl

 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)