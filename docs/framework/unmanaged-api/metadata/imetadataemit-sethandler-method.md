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
ms.openlocfilehash: 60c9266806ef6b5d7e2e1c3a219a4485bc22d7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445526"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler Yöntemi
Belirtilen tarafından başvurulan yöntemini ayarlar `IUnknown` işaretçi olarak belirteci yeniden harita oluşturma için bir bildirim geri çağırma.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pUnk`  
 [in] Kaydetmek için işleyici.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veri altyapısı tarafından sağlanan yöntemini kullanarak bildirim gönderir `SetHandler`, derleyicileri, oluşturmaz kayıtları iyileştirilmiş bir şekilde ve, istiyor kaydedilmiş kayıtları en iyi duruma getirmek için.  
  
 Geri çağırma yöntemi aracılığıyla sağlanmamışsa `SetHandler`, iyileştirme gerçekleştirilecek üzerinde kaydetme burada birkaç alma dışında kapsamları kullanarak birleştirildiğini `IMapToken` her kapsam için birleştirme üzerinde.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
