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
ms.openlocfilehash: d92129bd7c51ba2fa574f8337ba2b3727ab7b172
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599055"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="5b598-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b598-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="5b598-103">Belirtilen değiştirir `ManifestResource` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="5b598-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b598-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b598-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b598-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b598-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="5b598-106">[in] Belirten belirteç `ManifestResource` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="5b598-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="5b598-107">[in] Türde bir belirteç `File` veya `AssemblyRef`, kaynak sağlayıcıya eşler.</span><span class="sxs-lookup"><span data-stu-id="5b598-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="5b598-108">[in] Kaynak dosyası içinde başlangıcına uzaklık.</span><span class="sxs-lookup"><span data-stu-id="5b598-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="5b598-109">[in] Kaynak özniteliklerini belirten bayrağı değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="5b598-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b598-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b598-110">Remarks</span></span>  
 <span data-ttu-id="5b598-111">Oluşturmak için bir `ManifestResource` meta veri yapısı, kullanım [Imetadataassemblyemit::definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b598-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b598-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b598-112">Requirements</span></span>  
 <span data-ttu-id="5b598-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b598-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b598-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5b598-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b598-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5b598-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b598-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b598-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b598-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b598-117">See also</span></span>
- [<span data-ttu-id="5b598-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b598-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
