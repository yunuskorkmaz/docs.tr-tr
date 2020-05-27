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
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003990"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="77614-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77614-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="77614-103">Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.</span><span class="sxs-lookup"><span data-stu-id="77614-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77614-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="77614-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="77614-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77614-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="77614-106">'ndaki İçeri aktarma derlemesi için arabirim (imzanın tanımlandığı yer).</span><span class="sxs-lookup"><span data-stu-id="77614-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="77614-107">'ndaki Derlemenin karma blobu.</span><span class="sxs-lookup"><span data-stu-id="77614-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="77614-108">'ndaki İçindeki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="77614-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="77614-109">'ndaki İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="77614-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="77614-110">'ndaki İçeri aktarılacak imza.</span><span class="sxs-lookup"><span data-stu-id="77614-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="77614-111">'ndaki Bayt cinsinden boyutu `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="77614-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="77614-112">'ndaki Dışarı aktarma derlemesi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="77614-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="77614-113">'ndaki Dışarı aktarma meta verileri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="77614-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="77614-114">dışı Çevrilen imza blobunu tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="77614-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="77614-115">'ndaki Öğesinin bayt cinsinden kapasitesi `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="77614-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="77614-116">dışı Çevrilen İmzadaki gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77614-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77614-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77614-117">Requirements</span></span>  
 <span data-ttu-id="77614-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77614-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77614-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="77614-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77614-120">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="77614-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77614-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77614-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77614-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77614-122">See also</span></span>

- [<span data-ttu-id="77614-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77614-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="77614-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77614-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="77614-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77614-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="77614-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77614-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="77614-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77614-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
