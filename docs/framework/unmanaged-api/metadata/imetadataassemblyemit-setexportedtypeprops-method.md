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
ms.openlocfilehash: 076d027945dc27942e4b0989e14e86d829f76679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713498"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="511fc-102">IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="511fc-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="511fc-103">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="511fc-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511fc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="511fc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="511fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="511fc-105">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="511fc-106">'ndaki `ExportedType` Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="511fc-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="511fc-107">'ndaki `File` `AssemblyRef` `ExportedType` Bu türün nasıl uygulandığını belirten, veya türündeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="511fc-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="511fc-108">'ndaki `TypeDef` Kod dosyasında başvurulan belirteç.</span><span class="sxs-lookup"><span data-stu-id="511fc-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="511fc-109">'ndaki Türün özniteliklerini belirten bir bit düzeyinde değer birleşimi.</span><span class="sxs-lookup"><span data-stu-id="511fc-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="511fc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="511fc-110">Remarks</span></span>  

 <span data-ttu-id="511fc-111">`ExportedType`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="511fc-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511fc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="511fc-112">Requirements</span></span>  

 <span data-ttu-id="511fc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="511fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511fc-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="511fc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="511fc-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="511fc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="511fc-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="511fc-117">See also</span></span>

- [<span data-ttu-id="511fc-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="511fc-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
