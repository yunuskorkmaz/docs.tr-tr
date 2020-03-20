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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177688"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="036c7-102">IMetaDataEmit::DefineImportType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="036c7-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="036c7-103">Geçerli kapsam dışında tanımlanan belirtilen türe bir başvuru oluşturur ve bu başvuru için bir belirteç tanımlar.</span><span class="sxs-lookup"><span data-stu-id="036c7-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="036c7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="036c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="036c7-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="036c7-106">[içinde] Hedef türün içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyAlma](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="036c7-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="036c7-107">[içinde] Tarafından belirtilen derleme için karma içeren `pAssemImport`bir dizi.</span><span class="sxs-lookup"><span data-stu-id="036c7-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="036c7-108">[içinde] Dizideki `pbHashValue` bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="036c7-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="036c7-109">[içinde] Hedef türün içe aktarıldığı meta veri kapsamını temsil eden bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="036c7-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="036c7-110">[içinde] `mdTypeDef` Hedef türünü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="036c7-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="036c7-111">[içinde] Hedef türün içe aktarıldığı derlemeyi temsil eden bir [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="036c7-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="036c7-112">[çıkış] Tür `mdTypeRef` başvurusu için geçerli kapsamda tanımlanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="036c7-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="036c7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="036c7-113">Remarks</span></span>  
 <span data-ttu-id="036c7-114">[IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) yöntemini aramadan önce, `DefineImportType` geçerli kapsamda, üyenin üst sınıfı veya üst arabirimi için bir tür başvurusu oluşturmak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="036c7-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036c7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="036c7-115">Requirements</span></span>  
 <span data-ttu-id="036c7-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036c7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036c7-117">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="036c7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="036c7-118">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="036c7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="036c7-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036c7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036c7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="036c7-120">See also</span></span>

- [<span data-ttu-id="036c7-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="036c7-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="036c7-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="036c7-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
