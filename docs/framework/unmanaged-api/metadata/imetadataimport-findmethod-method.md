---
title: IMetaDataImport::FindMethod Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437890"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="d0cde-102">IMetaDataImport::FindMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0cde-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="d0cde-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span><span class="sxs-lookup"><span data-stu-id="d0cde-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0cde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0cde-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0cde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0cde-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d0cde-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span><span class="sxs-lookup"><span data-stu-id="d0cde-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="d0cde-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span><span class="sxs-lookup"><span data-stu-id="d0cde-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="d0cde-108">[in] The name of the method to search for.</span><span class="sxs-lookup"><span data-stu-id="d0cde-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d0cde-109">[in] A pointer to the binary metadata signature of the method.</span><span class="sxs-lookup"><span data-stu-id="d0cde-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d0cde-110">[in] The size in bytes of `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="d0cde-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d0cde-111">[out] A pointer to the matching MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="d0cde-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0cde-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0cde-112">Remarks</span></span>  
 <span data-ttu-id="d0cde-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="d0cde-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="d0cde-114">There might be multiple methods with the same name in a class or interface.</span><span class="sxs-lookup"><span data-stu-id="d0cde-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="d0cde-115">In that case, pass the method's signature to find the unique match.</span><span class="sxs-lookup"><span data-stu-id="d0cde-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="d0cde-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span><span class="sxs-lookup"><span data-stu-id="d0cde-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d0cde-117">A signature can embed a token that identifies the enclosing class or value type.</span><span class="sxs-lookup"><span data-stu-id="d0cde-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d0cde-118">The token is an index into the local TypeDef table.</span><span class="sxs-lookup"><span data-stu-id="d0cde-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="d0cde-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="d0cde-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="d0cde-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span><span class="sxs-lookup"><span data-stu-id="d0cde-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0cde-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0cde-121">Requirements</span></span>  
 <span data-ttu-id="d0cde-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0cde-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0cde-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0cde-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0cde-124">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0cde-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0cde-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0cde-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cde-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0cde-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="d0cde-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0cde-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d0cde-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0cde-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
