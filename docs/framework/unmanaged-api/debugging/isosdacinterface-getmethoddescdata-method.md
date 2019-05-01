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
ms.openlocfilehash: 4e32facc65162c4deb853cd507a00126e5f786e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914881"
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
**Kitaplığı:** Yok.  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [ISOSDacInterface arabirimi](isosdacinterface-interface.md)