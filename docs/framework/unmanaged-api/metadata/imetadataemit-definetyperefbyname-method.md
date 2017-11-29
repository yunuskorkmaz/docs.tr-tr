---
title: "IMetaDataEmit::DefineTypeRefByName Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName Yöntemi
Bir meta veri geçerli kapsamı dışında belirtilen kapsamda tanımlanan bir tür için belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tkResolutionScope`  
 [in] Çözümleme kapsamı belirleme belirteci. Aşağıdaki belirteç türlerini geçerlidir:  
  
-   `mdModuleRef`, türü arayanın tanımlanır aynı bütünleştirilmiş kodda tanımlanmış olması durumunda.  
  
-   `mdAssemblyRef`, türü arayanın tanımlanır farklı bir derlemede tanımlanmış olması durumunda.  
  
-   `mdTypeRef`, tür iç içe geçmiş tür ise.  
  
-   `mdModule`, türü arayanın tanımlanır modülünde tanımlanmış olması durumunda.  
  
-   Tür genel olarak tanımlanmışsa null.  
  
 `szName`  
 [in] Unicode hedef türünün adı.  
  
 `ptr`  
 [out] Bir işaretçi `mdTypeRef` türüne atanan belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Imetadataemit2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
