---
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
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503854"
---
# <a name="imetadataemitsetparent-method"></a>IMetaDataEmit::SetParent Yöntemi
Belirtilen üyenin [ımetadatayay::D efineMemberRef](imetadataemit-definememberref-method.md)öğesine yapılan önceki bir çağrı tarafından tanımlandığı gibi, belirtilen türün bir üyesi olduğunu ve [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md)'in bir önceki çağrısıyla tanımlanan bir üyesini olduğunu belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mr`  
 'ndaki `mdMemberRef`Yeni bir üst öğe alacak belirteç.  
  
 `tk`  
 'ndaki `mdToken`Yeni üst öğe için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
