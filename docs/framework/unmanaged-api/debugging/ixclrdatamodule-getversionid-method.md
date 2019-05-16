---
title: IXCLRDataModule::GetVersionId yöntemi
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
ms.openlocfilehash: 6ec18bcf079c7687df4ac9b7c5db23b84383c517
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632304"
---
# <a name="ixclrdatamodulegetversionid-method"></a>IXCLRDataModule::GetVersionId yöntemi

Modülün sürüm tanımlayıcısını alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a>Parametreler

`vid`\
[out] Modülün sürüm tanımlayıcısı.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 40th yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** None  
**Kitaplığı:** None  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)
