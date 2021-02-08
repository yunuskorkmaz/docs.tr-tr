---
description: ': IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi hakkında daha fazla bilgi edinin'
title: 'IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e01fe0737319a7b336d9f6992bf81b2c57f9e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800727"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a>IXCLRDataProcess:: Endenummethodınstancesbyaddress yöntemi

Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parametreler

`handle`\
dışı Metot örneklerini numaralandırmak için bir tanıtıcı.

## <a name="remarks"></a>Açıklamalar

Belirtilen yöntem arabirimin bir parçasıdır `IXCLRDataProcess` ve sanal yöntem tablosunun 30. yuvasına karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [CLRDataSourceType numaralandırması](clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](index.md)
- [IXCLRDataProcess Arabirimi](ixclrdataprocess-interface.md)
