---
title: IMetaDataEmit::DefineImportType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff0660ef2b30e32af540fe7bef5936ab6d0a359f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777629"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="043b6-102">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="043b6-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="043b6-103">Geçerli kapsam dışında tanımlanan ve bu başvuru için bir belirteç tanımlar belirtilen türe başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="043b6-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="043b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="043b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="043b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="043b6-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="043b6-106">[in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) içinden hedef türü alındığından derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="043b6-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="043b6-107">[in] Tarafından belirtilen derleme için karma içeren bir dizi `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="043b6-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="043b6-108">[in] Bayt sayısı `pbHashValue` dizisi.</span><span class="sxs-lookup"><span data-stu-id="043b6-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="043b6-109">[in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) içinden hedef türü alındığından meta veri kapsamı temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="043b6-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="043b6-110">[in] Bir `mdTypeDef` hedef türünü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="043b6-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="043b6-111">[in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) hedef türü alınan derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="043b6-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="043b6-112">[out] `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlı belirteç.</span><span class="sxs-lookup"><span data-stu-id="043b6-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="043b6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="043b6-113">Remarks</span></span>  
 <span data-ttu-id="043b6-114">Çağrılmadan önce [Imetadataemit::defineımportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) yöntemi kullanabileceğiniz `DefineImportType` üyenin üst sınıfta veya üst arabirimi için geçerli kapsam içinde bir tür başvurusu oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043b6-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="043b6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="043b6-115">Requirements</span></span>  
 <span data-ttu-id="043b6-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="043b6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="043b6-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="043b6-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="043b6-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="043b6-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="043b6-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="043b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="043b6-120">See also</span></span>

- [<span data-ttu-id="043b6-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="043b6-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="043b6-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="043b6-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
