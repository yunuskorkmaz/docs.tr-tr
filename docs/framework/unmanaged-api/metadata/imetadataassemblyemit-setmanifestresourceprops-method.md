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
ms.openlocfilehash: c46a3bc34ba7efa760e50416e9a6c39779727813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708935"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="b3208-102">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3208-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="b3208-103">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b3208-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3208-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b3208-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3208-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3208-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="b3208-106">'ndaki `ManifestResource` Değiştirilecek meta veri yapısını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="b3208-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="b3208-107">'ndaki `File` Kaynak sağlayıcısına eşlenen veya türündeki belirteç `AssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="b3208-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="b3208-108">'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="b3208-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="b3208-109">'ndaki Kaynak özniteliklerini belirleyen bayrak değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b3208-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3208-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3208-110">Remarks</span></span>  

 <span data-ttu-id="b3208-111">`ManifestResource`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3208-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3208-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3208-112">Requirements</span></span>  

 <span data-ttu-id="b3208-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3208-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3208-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b3208-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3208-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b3208-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3208-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3208-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3208-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3208-117">See also</span></span>

- [<span data-ttu-id="b3208-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3208-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
