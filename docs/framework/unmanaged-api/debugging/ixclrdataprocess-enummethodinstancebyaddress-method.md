---
title: IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d19a4b8116573f2ff6469fe612e7b7736651ff03
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354537"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess::EnumMethodInstanceByAddress yöntemi

Bu işlem bir adresi uzaklıkta başlayan yöntemi örneklerini sıralar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a>Parametreler

`handle`\
[in] Yöntem örnekleri numaralandırma tanıtıcısı.

`mod`\
[out] Numaralandırılmış yöntemi örneği.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 28 yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).   
**Üst bilgi:** Hiçbiri   
**Kitaplığı:** Hiçbiri   
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a>Ayrıca bkz.
- [CLRDataSourceType numaralandırması](clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](index.md)
- [IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)
