---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit:: SetManifestResourceProps Yöntemi'
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
ms.openlocfilehash: 0d5022c4acc562f9e77cec4ba080815db410862b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721038"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="85736-103">IMetaDataAssemblyEmit::SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85736-103">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="85736-104">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="85736-104">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85736-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85736-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85736-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85736-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="85736-107">'ndaki `ManifestResource` Değiştirilecek meta veri yapısını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="85736-107">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="85736-108">'ndaki `File` Kaynak sağlayıcısına eşlenen veya türündeki belirteç `AssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="85736-108">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="85736-109">'ndaki Dosyanın içindeki kaynağın başlangıcına olan Aralık.</span><span class="sxs-lookup"><span data-stu-id="85736-109">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="85736-110">'ndaki Kaynak özniteliklerini belirleyen bayrak değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="85736-110">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85736-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85736-111">Remarks</span></span>  

 <span data-ttu-id="85736-112">`ManifestResource`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="85736-112">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85736-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85736-113">Requirements</span></span>  

 <span data-ttu-id="85736-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85736-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85736-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="85736-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85736-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="85736-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85736-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85736-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85736-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85736-118">See also</span></span>

- [<span data-ttu-id="85736-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85736-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
