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
ms.openlocfilehash: 8a1cdff313dae73e3f5e8918ff2ef395c80b115d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490634"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="b6982-102">IMetaDataImport2::GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6982-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="b6982-103">Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="b6982-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6982-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b6982-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6982-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6982-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="b6982-106">'ndaki Meta verilerin döndürüleceği genel parametre kısıtlamasına yönelik belirteç.</span><span class="sxs-lookup"><span data-stu-id="b6982-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="b6982-107">dışı Kısıtlanmış genel parametreyi temsil eden belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6982-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="b6982-108">dışı Üzerinde bir kısıtlamayı temsil eden bir TypeDef, TypeRef veya TypeSpec belirteci işaretçisi `ptGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="b6982-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6982-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6982-109">Requirements</span></span>  
 <span data-ttu-id="b6982-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6982-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6982-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6982-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6982-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b6982-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6982-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6982-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6982-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6982-114">See also</span></span>

- [<span data-ttu-id="b6982-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6982-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="b6982-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6982-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
