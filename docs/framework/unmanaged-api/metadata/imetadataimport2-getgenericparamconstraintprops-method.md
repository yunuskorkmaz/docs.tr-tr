---
description: 'Daha fazla bilgi edinin: IMetaDataImport2:: GetGenericParamConstraintProps yöntemi'
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
ms.openlocfilehash: 03cc4df655f9ab7a1c04840e9d4fa782a90ce1ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688747"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="904aa-103">IMetaDataImport2::GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="904aa-103">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>

<span data-ttu-id="904aa-104">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="904aa-104">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904aa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="904aa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="904aa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="904aa-106">Parameters</span></span>  

 `gpc`  
 <span data-ttu-id="904aa-107">'ndaki Meta verilerin döndürüleceği genel parametre kısıtlamasına yönelik belirteç.</span><span class="sxs-lookup"><span data-stu-id="904aa-107">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="904aa-108">dışı Kısıtlanmış genel parametreyi temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="904aa-108">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="904aa-109">dışı Üzerinde bir kısıtlamayı temsil eden bir TypeDef, TypeRef veya TypeSpec belirteci işaretçisi `ptGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="904aa-109">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="904aa-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="904aa-110">Requirements</span></span>  

 <span data-ttu-id="904aa-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="904aa-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="904aa-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="904aa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="904aa-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="904aa-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="904aa-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="904aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904aa-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="904aa-115">See also</span></span>

- [<span data-ttu-id="904aa-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="904aa-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="904aa-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="904aa-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
