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
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175557"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="9bd36-102">IMetaDataEmit::TranslateSigWithScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bd36-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="9bd36-103">Geçerli kapsama bir derleme alır ve birleştirilmiş kapsam için yeni bir meta veri imzası alır.</span><span class="sxs-lookup"><span data-stu-id="9bd36-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9bd36-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bd36-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="9bd36-106">[içinde] Alma derlemesi için arabirim (imzanın tanımlandığı yer).</span><span class="sxs-lookup"><span data-stu-id="9bd36-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="9bd36-107">[içinde] Montaj için karma blob.</span><span class="sxs-lookup"><span data-stu-id="9bd36-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="9bd36-108">[içinde] Bayt `pbHashValue`sayısı.</span><span class="sxs-lookup"><span data-stu-id="9bd36-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="9bd36-109">[içinde] Alma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9bd36-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="9bd36-110">[içinde] Alınacak imza.</span><span class="sxs-lookup"><span data-stu-id="9bd36-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9bd36-111">[içinde] Boyutu, bayt, ve. `pbSigBlob`</span><span class="sxs-lookup"><span data-stu-id="9bd36-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="9bd36-112">[içinde] Dışa aktarma derlemesi için arayüz.</span><span class="sxs-lookup"><span data-stu-id="9bd36-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="9bd36-113">[içinde] Dışa aktarma meta veri kapsamı için arabirim.</span><span class="sxs-lookup"><span data-stu-id="9bd36-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="9bd36-114">[çıkış] Çevrilen imza blob tutmak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="9bd36-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="9bd36-115">[içinde] Kapasite, bayt, içinde. `pvTranslatedSig`</span><span class="sxs-lookup"><span data-stu-id="9bd36-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="9bd36-116">[çıkış] Çevrilen imzadaki gerçek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="9bd36-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd36-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bd36-117">Requirements</span></span>  
 <span data-ttu-id="9bd36-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd36-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd36-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bd36-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bd36-120">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9bd36-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bd36-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd36-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd36-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bd36-122">See also</span></span>

- [<span data-ttu-id="9bd36-123">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="9bd36-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="9bd36-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9bd36-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="9bd36-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bd36-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
