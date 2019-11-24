---
title: IMetaDataImport::GetParamProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437131"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="efff7-102">IMetaDataImport::GetParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="efff7-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="efff7-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="efff7-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efff7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efff7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efff7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efff7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="efff7-106">[in] A ParamDef token that represents the parameter to return metadata for.</span><span class="sxs-lookup"><span data-stu-id="efff7-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="efff7-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span><span class="sxs-lookup"><span data-stu-id="efff7-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="efff7-108">[out] The ordinal position of the parameter in the method argument list.</span><span class="sxs-lookup"><span data-stu-id="efff7-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="efff7-109">[out] A buffer to hold the name of the parameter.</span><span class="sxs-lookup"><span data-stu-id="efff7-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="efff7-110">[in] The requested size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="efff7-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="efff7-111">[out] The returned size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="efff7-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="efff7-112">[out] A pointer to any attribute flags associated with the parameter.</span><span class="sxs-lookup"><span data-stu-id="efff7-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="efff7-113">This is a bitmask of `CorParamAttr` values.</span><span class="sxs-lookup"><span data-stu-id="efff7-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="efff7-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="efff7-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="efff7-115">[out] A pointer to a constant string returned by the parameter.</span><span class="sxs-lookup"><span data-stu-id="efff7-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="efff7-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span><span class="sxs-lookup"><span data-stu-id="efff7-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efff7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efff7-117">Remarks</span></span>

<span data-ttu-id="efff7-118">The sequence values in `pulSequence` begin with 1 for parameters.</span><span class="sxs-lookup"><span data-stu-id="efff7-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="efff7-119">A return value has a sequence number of 0.</span><span class="sxs-lookup"><span data-stu-id="efff7-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="efff7-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efff7-120">Requirements</span></span>  
 <span data-ttu-id="efff7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efff7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efff7-122">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="efff7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efff7-123">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efff7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efff7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efff7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efff7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efff7-125">See also</span></span>

- [<span data-ttu-id="efff7-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efff7-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="efff7-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efff7-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
