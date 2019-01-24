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
ms.openlocfilehash: 825cb8ea94bee980f9e10b90cddf04db32c1a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491915"
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

`handle` [in] Yöntem örnekleri numaralandırma tanıtıcısı.

`mod` [out] Numaralandırılmış yöntemi örneği.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 28 yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).   
**Üst bilgi:** Hiçbiri   
**Kitaplığı:** Hiçbiri   
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a>Ayrıca bkz.
- [CLRDataSourceType numaralandırması](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataProcess arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
