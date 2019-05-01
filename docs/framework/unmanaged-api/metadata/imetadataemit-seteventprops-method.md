---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abfa8a3f58d3e9f7c80762c1faf2bc51514d71b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050044"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps Yöntemi
Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerinin [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ev`  
 [in] Olay belirteç.  
  
 `dwEventFlags`  
 [in] Olay bayrakları. Bu, bir bit maskesi, `CorEventAttr` değerleri.  
  
 `tkEventType`  
 [in] Olay sınıfı için belirteci. Bu bir `mdTypeDef` veya `mdTypeRef` belirteci.  
  
 `mdAddOn`  
 [in] Olay ya da null için abone olmak için kullanılan yöntem.  
  
 `mdRemoveOn`  
 [in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.  
  
 `mdFire`  
 [in] (Bir türetilmiş sınıf tarafından) olay oluşturmak için kullanılan yöntem.  
  
 `rmdOtherMethods[]`  
 [in] Olay ile ilişkili diğer yöntemleri için belirteçleri dizisi. Dizinin son öğesi olmalı `mdMethodDefNil`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
