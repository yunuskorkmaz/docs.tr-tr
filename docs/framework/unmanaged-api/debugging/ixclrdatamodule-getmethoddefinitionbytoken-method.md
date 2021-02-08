---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataModule:: GetMethodDefinitionByToken yöntemi'
title: 'IXCLRDataModule:: GetMethodDefinitionByToken yöntemi'
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
ms.openlocfilehash: 1eb1187d09183bfff97324a8032d23cbf471f580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800779"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a>IXCLRDataModule:: GetMethodDefinitionByToken yöntemi

Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.

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
'ndaki Yöntem belirteci.

`methodDefinition`\
dışı Yöntem tanımı.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataModule` ve sanal yöntem tablosunun 26. yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataModule Arabirimi](ixclrdatamodule-interface.md)
