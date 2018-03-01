---
title: IMetaDataEmit::Merge Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f05f2e39365b021e902b2bdaa41cda481b5af8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge Metodu
Belirtilen alınan kapsam birleştirilecek kapsamları listesine ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pImport`  
 [in] Bir işaretçi bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) birleştirilecek alınan kapsam tanımlayan nesne.  
  
 `pIMap`  
 [in] Bir işaretçi bir [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) belirteci yeniden eşleme belirtir nesnesi.  
  
 `pHandleer`  
 [in] Bir işaretçi bir <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` hataları belirten nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı [Imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) birleşme meta verilerin tek bir kapsam tetiklemek için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
