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
ms.openlocfilehash: 71029d6ebfb3248da791d4371dfe3e39589af443
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049997"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="9648f-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9648f-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="9648f-103">Bir derleme geçerli kapsam içeri aktarır ve yeni bir meta veri imzası birleştirilmiş kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="9648f-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9648f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9648f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9648f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9648f-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9648f-106">[in] Arabirim (imza tanımlandığı) alma derleme için.</span><span class="sxs-lookup"><span data-stu-id="9648f-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9648f-107">[in] Derleme için karma blob.</span><span class="sxs-lookup"><span data-stu-id="9648f-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9648f-108">[in] Bayt sayısı `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="9648f-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="9648f-109">[in] İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9648f-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="9648f-110">[in] İçeri aktarılacak imzası.</span><span class="sxs-lookup"><span data-stu-id="9648f-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9648f-111">[in] Bayt cinsinden boyutu, `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9648f-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9648f-112">[in] Dışarı aktarma derleme için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9648f-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="9648f-113">[in] Dışarı aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9648f-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="9648f-114">[out] Çevrilmiş imzası blob tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="9648f-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="9648f-115">[in] Bayt cinsinden kapasite, `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="9648f-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="9648f-116">[out] Çevrilmiş imzasında gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9648f-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9648f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9648f-117">Requirements</span></span>  
 <span data-ttu-id="9648f-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9648f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9648f-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9648f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9648f-120">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="9648f-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9648f-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9648f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9648f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9648f-122">See also</span></span>

- [<span data-ttu-id="9648f-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9648f-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="9648f-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9648f-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="9648f-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9648f-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9648f-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9648f-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="9648f-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9648f-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
