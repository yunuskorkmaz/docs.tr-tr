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
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723252"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="4e738-102">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e738-102">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="4e738-103">Geçerli kapsamın dışında tanımlanan belirtilen türe bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e738-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e738-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4e738-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e738-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e738-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="4e738-106">'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4e738-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4e738-107">'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="4e738-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4e738-108">'ndaki Dizideki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="4e738-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="4e738-109">'ndaki Hedef türün içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4e738-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="4e738-110">'ndaki `mdTypeDef` Hedef türünü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="4e738-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="4e738-111">'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4e738-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4e738-112">dışı `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="4e738-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e738-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e738-113">Remarks</span></span>  

 <span data-ttu-id="4e738-114">[Imetadatayay::D Efineımportmember](imetadataemit-defineimportmember-method.md) metodunu çağırmadan önce, `DefineImportType` üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e738-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e738-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e738-115">Requirements</span></span>  

 <span data-ttu-id="4e738-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e738-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e738-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4e738-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e738-118">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4e738-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e738-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e738-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e738-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e738-120">See also</span></span>

- [<span data-ttu-id="4e738-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e738-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4e738-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e738-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
