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
ms.workload: dotnet
ms.openlocfilehash: 2c860c4f2bf1991ca929d82ef3dec61f5d20a57d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="f36b5-102">IMetaDataImport2::GetGenericParamConstraintProps Metodu</span><span class="sxs-lookup"><span data-stu-id="f36b5-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="f36b5-103">Belirtilen kısıtlama belirtecin tarafından temsil edilen genel parametresini kısıtlaması ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f36b5-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f36b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f36b5-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f36b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f36b5-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="f36b5-106">[in] Meta verileri döndürmek üzere genel parametre kısıtlama belirteci.</span><span class="sxs-lookup"><span data-stu-id="f36b5-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="f36b5-107">[out] Sınırlı değildir genel parametresini temsil eden belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f36b5-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="f36b5-108">[out] Üzerinde bir kısıtlamayı temsil eden bir TypeDef, TypeRef veya TypeSpec'te belirteci için bir işaretçi `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="f36b5-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f36b5-109">Requirements</span></span>  
 <span data-ttu-id="f36b5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f36b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f36b5-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f36b5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f36b5-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f36b5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f36b5-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f36b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36b5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f36b5-114">See Also</span></span>  
 [<span data-ttu-id="f36b5-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36b5-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="f36b5-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36b5-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
