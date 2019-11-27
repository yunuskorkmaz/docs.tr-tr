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
ms.openlocfilehash: f6b5e12df60663b75e10b04eaa008a75d720d753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434435"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="42866-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42866-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="42866-103">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="42866-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42866-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42866-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42866-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42866-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="42866-106">'ndaki Değiştirilecek `ManifestResource` meta veri yapısını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="42866-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="42866-107">'ndaki Kaynak sağlayıcısına eşlenen `File` veya `AssemblyRef`türündeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="42866-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="42866-108">'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="42866-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="42866-109">'ndaki Kaynak özniteliklerini belirleyen bayrak değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="42866-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42866-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42866-110">Remarks</span></span>  
 <span data-ttu-id="42866-111">`ManifestResource` meta veri yapısı oluşturmak için [IMetaDataAssemblyEmit::D efineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="42866-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42866-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42866-112">Requirements</span></span>  
 <span data-ttu-id="42866-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42866-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42866-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="42866-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42866-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="42866-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42866-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42866-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42866-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42866-117">See also</span></span>

- [<span data-ttu-id="42866-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42866-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
