---
title: IMetaDataAssemblyImport::GetManifestResourceProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29458b0b7afa5a0c0be908915b4fc91c85d28c72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="238f0-102">IMetaDataAssemblyImport::GetManifestResourceProps Metodu</span><span class="sxs-lookup"><span data-stu-id="238f0-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="238f0-103">Belirtilen meta veri imzayla bildirim kaynağı özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="238f0-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="238f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="238f0-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="238f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="238f0-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="238f0-106">[in] Bir `mdManifestResource` özellikleri almak istediğiniz kaynağın temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="238f0-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="238f0-107">[out] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="238f0-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="238f0-108">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="238f0-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="238f0-109">[out] Gerçekte döndürülen geniş karakter sayısını gösteren bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="238f0-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="238f0-110">[out] Bir işaretçi bir `mdFile` belirteç veya bir `mdAssemblyRef` kaynağı içeren dosya veya derleme, sırasıyla temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="238f0-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="238f0-111">[out] Uzaklık dosyası içinde kaynak başına belirten bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="238f0-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="238f0-112">[out] Bir kaynağa uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="238f0-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="238f0-113">Bir veya birden çok bayrak değeri birleşimidir [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="238f0-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="238f0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="238f0-114">Requirements</span></span>  
 <span data-ttu-id="238f0-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="238f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="238f0-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="238f0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="238f0-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="238f0-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="238f0-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="238f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238f0-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="238f0-119">See Also</span></span>  
 [<span data-ttu-id="238f0-120">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="238f0-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
