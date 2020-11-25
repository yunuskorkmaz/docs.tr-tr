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
ms.openlocfilehash: 80d33da2eb2a7f0cfbe5dcb7279fff9973dada2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712930"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="b1339-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1339-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="b1339-103">Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.</span><span class="sxs-lookup"><span data-stu-id="b1339-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1339-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b1339-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b1339-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1339-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="b1339-106">'ndaki İçeri aktarma derlemesi için arabirim (imzanın tanımlandığı yer).</span><span class="sxs-lookup"><span data-stu-id="b1339-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="b1339-107">'ndaki Derlemenin karma blobu.</span><span class="sxs-lookup"><span data-stu-id="b1339-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="b1339-108">'ndaki İçindeki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="b1339-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="b1339-109">'ndaki İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1339-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="b1339-110">'ndaki İçeri aktarılacak imza.</span><span class="sxs-lookup"><span data-stu-id="b1339-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b1339-111">'ndaki Bayt cinsinden boyutu `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b1339-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="b1339-112">'ndaki Dışarı aktarma derlemesi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1339-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="b1339-113">'ndaki Dışarı aktarma meta verileri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="b1339-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="b1339-114">dışı Çevrilen imza blobunu tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="b1339-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="b1339-115">'ndaki Öğesinin bayt cinsinden kapasitesi `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="b1339-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="b1339-116">dışı Çevrilen İmzadaki gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b1339-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1339-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1339-117">Requirements</span></span>  

 <span data-ttu-id="b1339-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1339-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1339-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1339-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1339-120">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b1339-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1339-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1339-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1339-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1339-122">See also</span></span>

- [<span data-ttu-id="b1339-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1339-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="b1339-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1339-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b1339-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1339-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b1339-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1339-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b1339-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1339-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
