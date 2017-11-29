---
title: IMetaDataImport2::GetGenericParamConstraintProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetGenericParamConstraintProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d1e560dd511758652e1acbc262b4ddc3efdd12c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="7eecd-102">IMetaDataImport2::GetGenericParamConstraintProps Metodu</span><span class="sxs-lookup"><span data-stu-id="7eecd-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="7eecd-103">Belirtilen kısıtlama belirtecin tarafından temsil edilen genel parametresini kısıtlaması ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="7eecd-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eecd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7eecd-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eecd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7eecd-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="7eecd-106">[in] Meta verileri döndürmek üzere genel parametre kısıtlama belirteci.</span><span class="sxs-lookup"><span data-stu-id="7eecd-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="7eecd-107">[out] Sınırlı değildir genel parametresini temsil eden belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7eecd-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="7eecd-108">[out] Üzerinde bir kısıtlamayı temsil eden bir TypeDef, TypeRef veya TypeSpec'te belirteci için bir işaretçi `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="7eecd-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eecd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7eecd-109">Requirements</span></span>  
 <span data-ttu-id="7eecd-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eecd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eecd-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7eecd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7eecd-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7eecd-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7eecd-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eecd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eecd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7eecd-114">See Also</span></span>  
 [<span data-ttu-id="7eecd-115">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eecd-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="7eecd-116">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="7eecd-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
