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
ms.openlocfilehash: 9370b27fd385b0223b354365d64aa57048f4ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177835"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="350b6-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="350b6-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="350b6-103">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="350b6-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="350b6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="350b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="350b6-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="350b6-106">[içinde] Değiştirilecek `ManifestResource` meta veri yapısını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="350b6-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="350b6-107">[içinde] Kaynak sağlayıcısıyla eşlenebilen belirteç, tür `File` veya `AssemblyRef`kaynak sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="350b6-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="350b6-108">[içinde] Dosya içindeki kaynağın başına mahsup.</span><span class="sxs-lookup"><span data-stu-id="350b6-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="350b6-109">[içinde] Kaynağın özniteliklerini belirten bayrak değerlerinin bityişli bir leşimi.</span><span class="sxs-lookup"><span data-stu-id="350b6-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="350b6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="350b6-110">Remarks</span></span>  
 <span data-ttu-id="350b6-111">Meta `ManifestResource` veri yapısı oluşturmak için [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="350b6-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="350b6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="350b6-112">Requirements</span></span>  
 <span data-ttu-id="350b6-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="350b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="350b6-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="350b6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="350b6-115">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="350b6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="350b6-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="350b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350b6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="350b6-117">See also</span></span>

- [<span data-ttu-id="350b6-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="350b6-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
