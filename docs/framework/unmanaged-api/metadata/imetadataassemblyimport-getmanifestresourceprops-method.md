---
title: IMetaDataAssemblyImport::GetManifestResourceProps Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07237794ca45b16b1ae1ca95b1d62889f095350f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448165"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="1c8b1-102">IMetaDataAssemblyImport::GetManifestResourceProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1c8b1-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="1c8b1-103">Belirtilen meta veri imzayla bildirim kaynağı özelliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c8b1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1c8b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c8b1-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="1c8b1-106">[in] Bir `mdManifestResource` özellikleri almak istediğiniz kaynağın temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="1c8b1-107">[out] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1c8b1-108">[in] Geniş karakter boyutu, `szName`.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1c8b1-109">[out] Gerçekte döndürülen geniş karakter sayısını gösteren bir işaretçi `szName`.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="1c8b1-110">[out] Bir işaretçi bir `mdFile` belirteç veya bir `mdAssemblyRef` kaynağı içeren dosya veya derleme, sırasıyla temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="1c8b1-111">[out] Uzaklık dosyası içinde kaynak başına belirten bir değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="1c8b1-112">[out] Bir kaynağa uygulanan meta verileri açıklayan bayrakları gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="1c8b1-113">Bir veya birden çok bayrak değeri birleşimidir [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) değerleri.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c8b1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c8b1-114">Requirements</span></span>  
 <span data-ttu-id="1c8b1-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c8b1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c8b1-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c8b1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c8b1-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1c8b1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c8b1-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8b1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8b1-119">See Also</span></span>  
 [<span data-ttu-id="1c8b1-120">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c8b1-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
