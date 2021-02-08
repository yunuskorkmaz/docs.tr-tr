---
description: 'Şu konuda daha fazla bilgi edinin: IXCLRDataMethodDefinition:: Startenumınstances yöntemi'
title: 'IXCLRDataMethodDefinition:: Startenumınstances yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 74de6360c90766cfec17e6b88a495fe2a70858b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800831"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a>IXCLRDataMethodDefinition:: Startenumınstances yöntemi

Belirli bir için yöntem örneklerinin numaralandırması için bir tanıtıcı sağlar `IXCLRDataAppDomain` .

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>Parametreler

`appDomain`\
'ndaki Sabit listesi için bir uygulama etki alanı.

`handle`\
dışı Örnekleri numaralandırmak için bir tanıtıcı.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataMethodDefinition` ve sanal yöntem tablosunun 5 yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [CLRDataSourceType numaralandırması](clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](index.md)
- [IXCLRDataMethodDefinition Arabirimi](ixclrdatamethoddefinition-interface.md)
