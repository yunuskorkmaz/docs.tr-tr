---
title: IMetaDataEmit::Merge Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448060"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge Yöntemi
Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pImport`  
 'ndaki Birleştirilecek kapsamı tanımlayan bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) nesnesine yönelik işaretçi.  
  
 `pIMap`  
 'ndaki Belirteç yeniden eşlemesini belirten bir [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) nesnesine yönelik işaretçi.  
  
 `pHandler`  
 'ndaki Hataları belirten [IUnknown](/cpp/atl/iunknown) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta verilerin birleştiğini tek bir kapsamda tetiklemek için [ımetadatayayma:: MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) ' i çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
