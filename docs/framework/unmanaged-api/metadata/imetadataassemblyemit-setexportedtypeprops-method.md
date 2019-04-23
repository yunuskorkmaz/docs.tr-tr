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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c09140488730179616d11932faa3542f704958a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123753"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="59721-102">IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59721-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="59721-103">Belirtilen değiştirir `ExportedType` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="59721-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59721-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59721-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59721-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59721-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="59721-106">[in] Belirten bir meta veri belirteci `ExportedType` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="59721-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="59721-107">[in] Türde bir belirteç `File`, `AssemblyRef`, veya `ExportedType`, bu tür nasıl uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59721-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="59721-108">[in] `TypeDef` Kod dosyasında başvurulan bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="59721-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="59721-109">[in] Türü özniteliklerini belirten değerlerinin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="59721-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59721-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59721-110">Remarks</span></span>  
 <span data-ttu-id="59721-111">Oluşturmak için bir `ExportedType` meta veri yapısı, kullanım [Imetadataassemblyemit::defineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="59721-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59721-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59721-112">Requirements</span></span>  
 <span data-ttu-id="59721-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59721-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59721-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="59721-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59721-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="59721-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59721-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59721-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59721-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59721-117">See also</span></span>

- [<span data-ttu-id="59721-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59721-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
