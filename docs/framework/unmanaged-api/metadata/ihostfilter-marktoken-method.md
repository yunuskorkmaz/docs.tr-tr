---
title: IHostFilter::MarkToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f486ffd1206dd30fa29d3f07c8c5b738cc207db0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745864"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken Yöntemi
Belirtilen meta veri belirteci işleneceğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [in] İşlenecek meta veri belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, meta veri kapsamları dahilinde olması durumunda bir belirteç istersiniz. `MarkToken` Yöntemi meta veri altyapısı geçirilir [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IHostFilter Arabirimi](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
