---
title: IMetaDataEmit::SetHandler Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac0e5db4a87b49d631bad4411f03fae8c1199aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050031"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler Yöntemi
Belirtilen tarafından başvurulan ayarlar `IUnknown` bir bildirim geri çağırması için belirteci yeniden eşleme olarak işaretçi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pUnk`  
 [in] Kaydetmek için işleyici.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri altyapısı tarafından sağlanan yöntemini kullanarak bildirim gönderir. `SetHandler`, derleyiciler, oluşturmaz kayıtları en iyi duruma getirilmiş bir yolla ve kaydedilmiş kayıtları en iyi hale getirmek istediğiniz için.  
  
 Geri çağırma yöntemi aracılığıyla sağlanmazsa `SetHandler`, hiçbir iyileştirme gerçekleştirilecek üzerinde kaydetme burada birkaç alma dışında kapsamları kullanarak birleştirildiğini `IMapToken` üzerinde her kapsam için birleştirme.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
