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
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008228"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken Yöntemi
Belirtilen meta veri belirtecinin işleneceğini belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 'ndaki İşlenecek meta veri belirteci.  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, meta veri kapsamlarındaki bir belirtecin işlenmesini istersiniz. `MarkToken`Yöntemi, [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) yöntemi aracılığıyla meta veri altyapısına geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IHostFilter Arabirimi](ihostfilter-interface.md)
