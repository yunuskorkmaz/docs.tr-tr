---
title: IXCLRDataProcess::EnumModule yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769574"
---
# <a name="ixclrdataprocessenummodule-method"></a>IXCLRDataProcess::EnumModule yöntemi

Bu işlemin modülleri numaralandırır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a>Parametreler

`handle`\
[out içinde] Modülleri numaralandırma tanıtıcısı.

`mod`\
[out] Numaralandırılmış modülü.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve 25 sanal yöntem tablosunu yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** None  
**Kitaplığı:** Yok.  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [CLRDataSourceType numaralandırması](clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](index.md)
- [IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)
- [IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)
