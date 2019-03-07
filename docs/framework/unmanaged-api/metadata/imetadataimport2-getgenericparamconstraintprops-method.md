---
title: IMetaDataImport2::GetGenericParamConstraintProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c9db8a7caa13543b6bc1351d50bf34cf7fb328f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479070"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="fae49-102">IMetaDataImport2::GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fae49-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="fae49-103">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlama ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="fae49-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fae49-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fae49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fae49-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="fae49-106">[in] Genel parametre kısıtlama meta verileri döndürülecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="fae49-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="fae49-107">[out] Kısıtlı genel parametreyi temsil eden bir belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fae49-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="fae49-108">[out] Bir işaretçi üzerinde bir kısıtlamayı temsil eden bir tür tanımı, TypeRef veya TypeSpec'te belirteci `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="fae49-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae49-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fae49-109">Requirements</span></span>  
 <span data-ttu-id="fae49-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fae49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae49-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fae49-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fae49-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="fae49-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fae49-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae49-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fae49-114">See also</span></span>
- [<span data-ttu-id="fae49-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fae49-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="fae49-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fae49-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
