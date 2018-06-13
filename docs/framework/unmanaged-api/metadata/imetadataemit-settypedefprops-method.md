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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b72088e4aa9994ca6ae411ec36d4c578e3017e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447889"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="97254-102">IMetaDataEmit::SetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97254-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="97254-103">Önceki bir çağrı tarafından tanımlanan bir türü özelliklerini ayarlar [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="97254-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97254-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97254-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97254-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97254-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="97254-106">[in] Bir `mdTypeDef` belirteç elde özgün çağrıya [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="97254-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="97254-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="97254-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="97254-108">Bu, bir bit maskesi olan `CorTypeAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="97254-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="97254-109">[in] `mdToken` Temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="97254-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="97254-110">Önceki çağrısından alınan [Imetadataemit::defineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), veya `null`.</span><span class="sxs-lookup"><span data-stu-id="97254-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="97254-111">[in] Bu tür uygulayan arabirimler için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="97254-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="97254-112">Bunlar `mdTypeRef` belirteçleri elde edilir kullanarak [Imetadataemit::defineımporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="97254-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="97254-113">Dizinin son öğesi olmalı `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="97254-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97254-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97254-114">Requirements</span></span>  
 <span data-ttu-id="97254-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97254-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97254-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="97254-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97254-117">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="97254-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97254-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97254-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97254-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97254-119">See Also</span></span>  
 [<span data-ttu-id="97254-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97254-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="97254-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97254-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
