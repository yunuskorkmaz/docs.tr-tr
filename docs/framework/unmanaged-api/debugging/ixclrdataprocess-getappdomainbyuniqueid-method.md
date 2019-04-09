---
title: IXCLRDataProcess::GetAppDomainByUniqueId Method
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 257fa2cf03a62ea888b76519aa5c9f9e84038045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126509"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>IXCLRDataProcess::GetAppDomainByUniqueId Method

Alır bir `AppDomain` bir işlemde kendi benzersiz tanımlayıcısına göre.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi
```
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a>Parametreler

`id`\
[in] AppDomain benzersiz tanımlayıcısı

`appDomain`\
[out] Uygulama etki alanı

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataProcess` arabirim ve sanal yöntem tablosunu 20 yuvaya karşılık gelir. `IXCLRDataAppDomain*` Döndürülen diğer API'ler ile etkileşim için kullanılır.

## <a name="requirements"></a>Gereksinimler
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
**Üst bilgi:** Yok.  
**Kitaplığı:** Yok.  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataProcess Arabirimi](ixclrdataprocess-interface.md)
