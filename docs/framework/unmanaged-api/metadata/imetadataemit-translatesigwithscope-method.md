---
title: "IMetaDataEmit::TranslateSigWithScope Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="f39d2-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f39d2-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="f39d2-103">Bir derlemeyi geçerli kapsam alır ve yeni bir meta veri imza için birleştirilmiş kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="f39d2-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f39d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f39d2-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="f39d2-106">[in] İçeri aktarma derleme için (imza tanımlandığı) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f39d2-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f39d2-107">[in] Derleme için karma blob.</span><span class="sxs-lookup"><span data-stu-id="f39d2-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f39d2-108">[in] Bayt sayısı `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f39d2-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="f39d2-109">[in] İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f39d2-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="f39d2-110">[in] İçeri aktarılacak imzası.</span><span class="sxs-lookup"><span data-stu-id="f39d2-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f39d2-111">[in] Bayt olarak boyutu, `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f39d2-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f39d2-112">[in] Dışarı aktarma derleme için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f39d2-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="f39d2-113">[in] Dışarı aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="f39d2-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="f39d2-114">[out] Çevrilen imzası blob tutacak bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f39d2-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="f39d2-115">[in] Bayt cinsinden kapasite, `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="f39d2-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="f39d2-116">[out] Çevrilen imzada gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="f39d2-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f39d2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f39d2-117">Requirements</span></span>  
 <span data-ttu-id="f39d2-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f39d2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f39d2-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f39d2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f39d2-120">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f39d2-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f39d2-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f39d2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39d2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f39d2-122">See Also</span></span>  
 [<span data-ttu-id="f39d2-123">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="f39d2-124">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="f39d2-125">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f39d2-126">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="f39d2-127">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="f39d2-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
