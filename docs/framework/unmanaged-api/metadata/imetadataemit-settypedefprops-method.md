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
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177458"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="31f1b-102">IMetaDataEmit::SetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31f1b-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="31f1b-103">[IMetaDataEmit::DefineTypeDef'e](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)yapılan bir önceki çağrıyla tanımlanan bir türün özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="31f1b-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31f1b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31f1b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="31f1b-106">[içinde] IMetaDataEmit orijinal arama elde edilen bir `mdTypeDef` belirteç::DefineTypeDef . [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)</span><span class="sxs-lookup"><span data-stu-id="31f1b-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="31f1b-107">[içinde] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="31f1b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="31f1b-108">Bu `CorTypeAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="31f1b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="31f1b-109">[içinde] Taban `mdToken` sınıfın.</span><span class="sxs-lookup"><span data-stu-id="31f1b-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="31f1b-110">[IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), veya `null`.</span><span class="sxs-lookup"><span data-stu-id="31f1b-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="31f1b-111">[içinde] Bu tür uygular arabirimleri için belirteçleri bir dizi.</span><span class="sxs-lookup"><span data-stu-id="31f1b-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="31f1b-112">Bu `mdTypeRef` belirteçler [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="31f1b-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="31f1b-113">Dizinin son öğesi olmalıdır. `mdTokenNil`</span><span class="sxs-lookup"><span data-stu-id="31f1b-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f1b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31f1b-114">Requirements</span></span>  
 <span data-ttu-id="31f1b-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f1b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f1b-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31f1b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31f1b-117">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="31f1b-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31f1b-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f1b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f1b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31f1b-119">See also</span></span>

- [<span data-ttu-id="31f1b-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f1b-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="31f1b-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f1b-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
