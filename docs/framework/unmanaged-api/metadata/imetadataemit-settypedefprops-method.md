---
title: IMetaDataEmit::SetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 3ab29fc8c983b354ad5088d26c547868940ec70a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447722"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="b034e-102">IMetaDataEmit::SetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b034e-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="b034e-103">[Imetadatayay::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b034e-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b034e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b034e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b034e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b034e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b034e-106">'ndaki Imetadatayayma için özgün çağrıdan alınan bir `mdTypeDef` belirteci [::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="b034e-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="b034e-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b034e-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="b034e-108">Bu, `CorTypeAttr` değerlerinin bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="b034e-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="b034e-109">'ndaki Temel sınıfın `mdToken`.</span><span class="sxs-lookup"><span data-stu-id="b034e-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="b034e-110">Imetadatayayma için önceki bir çağrıdan alındı [::D Efineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)veya `null`.</span><span class="sxs-lookup"><span data-stu-id="b034e-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="b034e-111">'ndaki Bu türün uyguladığı arabirimler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="b034e-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="b034e-112">Bu `mdTypeRef` belirteçleri [ımetadatayayma::D Efineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="b034e-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="b034e-113">Dizinin son öğesi `mdTokenNil`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b034e-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b034e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b034e-114">Requirements</span></span>  
 <span data-ttu-id="b034e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b034e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b034e-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b034e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b034e-117">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b034e-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b034e-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b034e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b034e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b034e-119">See also</span></span>

- [<span data-ttu-id="b034e-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b034e-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b034e-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b034e-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
