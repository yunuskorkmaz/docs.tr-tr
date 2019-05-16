---
title: ISOSDacInterface::GetMethodDescData yöntemi
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cdbf662c664d6c87b2fa17bcb10d735b0f573dd2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632311"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface::GetMethodDescData yöntemi

Verileri için belirli MethodDesc işaretçi alır.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Parametreler

`methodDesc`\
[in] MethodDesc adresi.

`ip`\
[in] Yöntem IP adresi.

`data`\
[out] İç API'lerinden döndürülen MethodDesc ile ilişkili veriler.

`cRevertedRejitVersions`\
[out] Geri döndürülen rejit sürüm sayısı.

`rgRevertedRejitData`\
[out] İç API'lerinden döndürülen şekilde geri döndürülen rejit sürümleriyle ilişkili veriler.

`pcNeededRevertedRejitData`\
[out] Geri döndürülen ReJit sürümleriyle ilişkili verileri depolamak için gereken bayt sayısı.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `ISOSDacInterface` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir. Kullanmaya devam edebilmek için [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) 64-bit işaretsiz tamsayı tanımlanması gerekir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** None  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [ISOSDacInterface arabirimi](isosdacinterface-interface.md)
