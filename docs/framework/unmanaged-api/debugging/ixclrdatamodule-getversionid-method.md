---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataModule:: Getversionıd yöntemi'
title: 'IXCLRDataModule:: Getversionıd yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b924757f43d106df555ea028270ac873f8f4558
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800766"
---
# <a name="ixclrdatamodulegetversionid-method"></a>IXCLRDataModule:: Getversionıd yöntemi

Modülün sürüm tanımlayıcısını alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a>Parametreler

`vid`\
dışı Modülün sürüm tanımlayıcısı.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 41 yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataModule Arabirimi](ixclrdatamodule-interface.md)
