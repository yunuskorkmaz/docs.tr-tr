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
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722017"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge Yöntemi

Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pImport`  
 'ndaki Birleştirilecek kapsamı tanımlayan bir [IMetaDataImport](imetadataimport-interface.md) nesnesine yönelik işaretçi.  
  
 `pIMap`  
 'ndaki Belirteç yeniden eşlemesini belirten bir [IMapToken](imaptoken-interface.md) nesnesine yönelik işaretçi.  
  
 `pHandler`  
 'ndaki Hataları belirten [IUnknown](/cpp/atl/iunknown) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Meta verilerin birleştiğini tek bir kapsamda tetiklemek için [ımetadatayayma:: MergeEnd](imetadataemit-mergeend-method.md) ' i çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
