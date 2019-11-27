---
title: IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: ae682c354a7a5188611b103008a3e18f8d821260
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431933"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="c10cc-102">IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c10cc-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="c10cc-103">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c10cc-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c10cc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c10cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c10cc-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="c10cc-106">'ndaki Değiştirilecek `ExportedType` meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c10cc-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="c10cc-107">'ndaki Bu türün nasıl uygulandığını belirten `File`, `AssemblyRef`veya `ExportedType`türündeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="c10cc-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="c10cc-108">'ndaki Kod dosyasında başvurulan `TypeDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="c10cc-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="c10cc-109">'ndaki Türün özniteliklerini belirten bir bit düzeyinde değer birleşimi.</span><span class="sxs-lookup"><span data-stu-id="c10cc-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c10cc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c10cc-110">Remarks</span></span>  
 <span data-ttu-id="c10cc-111">`ExportedType` meta veri yapısı oluşturmak için [IMetaDataAssemblyEmit::D efineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c10cc-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c10cc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c10cc-112">Requirements</span></span>  
 <span data-ttu-id="c10cc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c10cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c10cc-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c10cc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c10cc-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c10cc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c10cc-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c10cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c10cc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c10cc-117">See also</span></span>

- [<span data-ttu-id="c10cc-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c10cc-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
