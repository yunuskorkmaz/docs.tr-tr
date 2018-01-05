---
title: "IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6649b8f82031699692a0929b5483ba57147399b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="dc041-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc041-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="dc041-103">Belirtilen değiştirir `ManifestResource` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="dc041-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc041-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc041-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc041-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc041-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="dc041-106">[in] Belirtir belirteci `ManifestResource` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="dc041-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="dc041-107">[in] Türünde belirteç `File` veya `AssemblyRef`, kaynak sağlayıcısı eşler.</span><span class="sxs-lookup"><span data-stu-id="dc041-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="dc041-108">[in] Dosyası içinde kaynak başına uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="dc041-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="dc041-109">[in] Kaynak özniteliklerini belirtmek bayrağı değerlerin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="dc041-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc041-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc041-110">Remarks</span></span>  
 <span data-ttu-id="dc041-111">Oluşturmak için bir `ManifestResource` meta veri yapısı, kullanım [Imetadataassemblyemit::definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dc041-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc041-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc041-112">Requirements</span></span>  
 <span data-ttu-id="dc041-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc041-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc041-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc041-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc041-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dc041-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc041-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc041-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc041-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc041-117">See Also</span></span>  
 [<span data-ttu-id="dc041-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc041-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
