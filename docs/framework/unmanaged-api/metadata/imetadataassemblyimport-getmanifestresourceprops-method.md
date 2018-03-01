---
title: IMetaDataAssemblyImport::GetManifestResourceProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ba9af4abca111b94a678c48d236a53dc6313b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="1a4f9-102">IMetaDataAssemblyImport::GetManifestResourceProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1a4f9-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="1a4f9-103">Belirtilen meta veri imzayla bildirim kaynağı özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a4f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a4f9-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1a4f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a4f9-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="1a4f9-106">[in] Bir `mdManifestResource` özellikleri almak istediğiniz kaynağın temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="1a4f9-107">[out] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1a4f9-108">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1a4f9-109">[out] Gerçekte döndürülen geniş karakter sayısını gösteren bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="1a4f9-110">[out] Bir işaretçi bir `mdFile` belirteç veya bir `mdAssemblyRef` kaynağı içeren dosya veya derleme, sırasıyla temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="1a4f9-111">[out] Uzaklık dosyası içinde kaynak başına belirten bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="1a4f9-112">[out] Bir kaynağa uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="1a4f9-113">Bir veya birden çok bayrak değeri birleşimidir [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a4f9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a4f9-114">Requirements</span></span>  
 <span data-ttu-id="1a4f9-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a4f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a4f9-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a4f9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a4f9-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1a4f9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a4f9-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4f9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a4f9-119">See Also</span></span>  
 [<span data-ttu-id="1a4f9-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a4f9-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
