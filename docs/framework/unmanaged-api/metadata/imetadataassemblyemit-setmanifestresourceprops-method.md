---
title: IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6fbc3f41e95730e93bd907762dd8cd4205037c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187310"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="f6214-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6214-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="f6214-103">Belirtilen değiştirir `ManifestResource` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="f6214-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6214-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6214-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6214-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6214-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="f6214-106">[in] Belirten belirteç `ManifestResource` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="f6214-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="f6214-107">[in] Türde bir belirteç `File` veya `AssemblyRef`, kaynak sağlayıcıya eşler.</span><span class="sxs-lookup"><span data-stu-id="f6214-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="f6214-108">[in] Kaynak dosyası içinde başlangıcına uzaklık.</span><span class="sxs-lookup"><span data-stu-id="f6214-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="f6214-109">[in] Kaynak özniteliklerini belirten bayrağı değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f6214-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6214-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6214-110">Remarks</span></span>  
 <span data-ttu-id="f6214-111">Oluşturmak için bir `ManifestResource` meta veri yapısı, kullanım [Imetadataassemblyemit::definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f6214-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6214-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6214-112">Requirements</span></span>  
 <span data-ttu-id="f6214-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6214-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6214-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f6214-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6214-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="f6214-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f6214-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f6214-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6214-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6214-117">See also</span></span>

- [<span data-ttu-id="f6214-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6214-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
