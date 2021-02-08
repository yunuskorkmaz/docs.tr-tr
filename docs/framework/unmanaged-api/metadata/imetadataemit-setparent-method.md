---
description: ': Imetadatayayma:: SetParent yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetParent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: 9025d4a37de85a0e657059f63ef781dc4377c036
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772009"
---
# <a name="imetadataemitsetparent-method"></a>IMetaDataEmit::SetParent Yöntemi

Belirtilen üyenin [ımetadatayay::D efineMemberRef](imetadataemit-definememberref-method.md)öğesine yapılan önceki bir çağrı tarafından tanımlandığı gibi, belirtilen türün bir üyesi olduğunu ve [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md)'in bir önceki çağrısıyla tanımlanan bir üyesini olduğunu belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mr`  
 'ndaki `mdMemberRef` Yeni bir üst öğe alacak belirteç.  
  
 `tk`  
 'ndaki `mdToken` Yeni üst öğe için.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
