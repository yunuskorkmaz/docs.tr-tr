---
title: "IMetaDataEmit::DefineImportType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fee13c88cc39398808ad1ff481e602d63e8f39f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="db660-102">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db660-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="db660-103">Geçerli kapsamı dışında tanımlanır ve bu başvurusu için bir belirteç tanımlayan belirtilen türüne bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db660-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db660-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db660-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="db660-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db660-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="db660-106">[in] Bir [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) , hedef türü alındığından derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="db660-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="db660-107">[in] Belirtilen derleme için karma içeren bir dizi `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="db660-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="db660-108">[in] Bayt sayısı `pbHashValue` dizi.</span><span class="sxs-lookup"><span data-stu-id="db660-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="db660-109">[in] Bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , hedef türü alındığından meta veri kapsamı temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="db660-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="db660-110">[in] Bir `mdTypeDef` belirteci hedef türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="db660-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="db660-111">[in] Bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) içine hedef türü alındığından derleme temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="db660-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="db660-112">[out] `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlı belirteci.</span><span class="sxs-lookup"><span data-stu-id="db660-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db660-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db660-113">Remarks</span></span>  
 <span data-ttu-id="db660-114">Çağrılmadan önce [Imetadataemit::defineımportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) kullanabileceğiniz yöntemi, `DefineImportType` üyenin üst sınıf veya üst arabirimi için geçerli kapsam içinde bir tür başvurusu oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="db660-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db660-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db660-115">Requirements</span></span>  
 <span data-ttu-id="db660-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db660-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db660-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db660-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db660-118">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="db660-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db660-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db660-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db660-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db660-120">See Also</span></span>  
 [<span data-ttu-id="db660-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db660-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="db660-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db660-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
