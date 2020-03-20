---
title: IXCLRDataModule::GetMethodDefinitionByToken Yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176675"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a>IXCLRDataModule::GetMethodDefinitionByToken Yöntemi

Belirli bir meta veri belirtecikarşılık gelen yöntem tanımıalır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a>Parametreler

`token`\
[içinde] Yöntem belirteci.

`methodDefinition`\
[çıkış] Yöntem tanımı.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem `IXCLRDataModule` arabirimin bir parçasıdır ve sanal yöntem tablosunun 25 yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üstbilgi:** Hiçbiri  
**Kütüphane:** Hiçbiri  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama](index.md)
- [IXCLRDataModule Arabirimi](ixclrdatamodule-interface.md)
