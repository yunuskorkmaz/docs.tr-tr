---
title: IMetaDataEmit::TranslateSigWithScope Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ddaddbbd050dc079fcf20551e90c895d2f4ef59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446349"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="e1211-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1211-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="e1211-103">Bir derlemeyi geçerli kapsam alır ve yeni bir meta veri imza için birleştirilmiş kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="e1211-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1211-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1211-104">Syntax</span></span>  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1211-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1211-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="e1211-106">[in] İçeri aktarma derleme için (imza tanımlandığı) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e1211-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e1211-107">[in] Derleme için karma blob.</span><span class="sxs-lookup"><span data-stu-id="e1211-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e1211-108">[in] Bayt sayısı `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e1211-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="e1211-109">[in] İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e1211-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="e1211-110">[in] İçeri aktarılacak imzası.</span><span class="sxs-lookup"><span data-stu-id="e1211-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e1211-111">[in] Bayt olarak boyutu, `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="e1211-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="e1211-112">[in] Dışarı aktarma derleme için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e1211-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="e1211-113">[in] Dışarı aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e1211-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="e1211-114">[out] Çevrilen imzası blob tutacak bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="e1211-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="e1211-115">[in] Bayt cinsinden kapasite, `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="e1211-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="e1211-116">[out] Çevrilen imzada gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e1211-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1211-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1211-117">Requirements</span></span>  
 <span data-ttu-id="e1211-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1211-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1211-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1211-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1211-120">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e1211-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1211-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1211-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1211-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1211-122">See Also</span></span>  
 [<span data-ttu-id="e1211-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1211-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="e1211-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1211-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="e1211-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1211-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e1211-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1211-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="e1211-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1211-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
