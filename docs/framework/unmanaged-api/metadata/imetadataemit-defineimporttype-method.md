---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D Efineımporttype yöntemi'
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
ms.openlocfilehash: 7afe0fe400e4eb6e177a06e00b2d69202820804c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753438"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="683a4-103">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="683a4-103">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="683a4-104">Geçerli kapsamın dışında tanımlanan belirtilen türe bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="683a4-104">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="683a4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="683a4-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="683a4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="683a4-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="683a4-107">'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="683a4-107">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="683a4-108">'ndaki Tarafından belirtilen derlemenin karmasını içeren bir dizi `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="683a4-108">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="683a4-109">'ndaki Dizideki bayt sayısı `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="683a4-109">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="683a4-110">'ndaki Hedef türün içeri aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="683a4-110">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="683a4-111">'ndaki `mdTypeDef` Hedef türünü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="683a4-111">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="683a4-112">'ndaki Hedef türün içeri aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="683a4-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="683a4-113">dışı `mdTypeRef` Tür başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="683a4-113">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="683a4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="683a4-114">Remarks</span></span>  

 <span data-ttu-id="683a4-115">[Imetadatayay::D Efineımportmember](imetadataemit-defineimportmember-method.md) metodunu çağırmadan önce, `DefineImportType` üyenin üst sınıfı veya üst arabirimi için geçerli kapsamda bir tür başvurusu oluşturmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="683a4-115">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="683a4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="683a4-116">Requirements</span></span>  

 <span data-ttu-id="683a4-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="683a4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="683a4-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="683a4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="683a4-119">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="683a4-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="683a4-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="683a4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683a4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="683a4-121">See also</span></span>

- [<span data-ttu-id="683a4-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="683a4-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="683a4-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="683a4-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
