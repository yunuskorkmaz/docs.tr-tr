---
description: ': Imetadatayayma:: TranslateSigWithScope yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e5f4e522e993f2f391ca0c29e5fcc2cbb71775e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720940"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="125c9-103">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="125c9-103">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="125c9-104">Bir derlemeyi geçerli kapsama aktarır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.</span><span class="sxs-lookup"><span data-stu-id="125c9-104">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="125c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="125c9-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="125c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="125c9-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="125c9-107">'ndaki İçeri aktarma derlemesi için arabirim (imzanın tanımlandığı yer).</span><span class="sxs-lookup"><span data-stu-id="125c9-107">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="125c9-108">'ndaki Derlemenin karma blobu.</span><span class="sxs-lookup"><span data-stu-id="125c9-108">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="125c9-109">'ndaki İçindeki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="125c9-109">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="125c9-110">'ndaki İçeri aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="125c9-110">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="125c9-111">'ndaki İçeri aktarılacak imza.</span><span class="sxs-lookup"><span data-stu-id="125c9-111">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="125c9-112">'ndaki Bayt cinsinden boyutu `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="125c9-112">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="125c9-113">'ndaki Dışarı aktarma derlemesi için arabirim.</span><span class="sxs-lookup"><span data-stu-id="125c9-113">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="125c9-114">'ndaki Dışarı aktarma meta verileri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="125c9-114">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="125c9-115">dışı Çevrilen imza blobunu tutan arabellek.</span><span class="sxs-lookup"><span data-stu-id="125c9-115">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="125c9-116">'ndaki Öğesinin bayt cinsinden kapasitesi `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="125c9-116">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="125c9-117">dışı Çevrilen İmzadaki gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="125c9-117">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="125c9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="125c9-118">Requirements</span></span>  

 <span data-ttu-id="125c9-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="125c9-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="125c9-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="125c9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="125c9-121">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="125c9-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="125c9-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="125c9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125c9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="125c9-123">See also</span></span>

- [<span data-ttu-id="125c9-124">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="125c9-124">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="125c9-125">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="125c9-125">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="125c9-126">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="125c9-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="125c9-127">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="125c9-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="125c9-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="125c9-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
