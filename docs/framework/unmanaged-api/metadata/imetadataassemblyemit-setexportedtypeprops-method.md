---
description: ': IMetaDataAssemblyEmit:: SetExportedTypeProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 61032abd7b049af29c583e9aee126184af3c78f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678126"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="57240-103">IMetaDataAssemblyEmit::SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57240-103">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="57240-104">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="57240-104">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57240-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57240-105">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57240-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57240-106">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="57240-107">'ndaki `ExportedType` Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="57240-107">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="57240-108">'ndaki `File` `AssemblyRef` `ExportedType` Bu türün nasıl uygulandığını belirten, veya türündeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="57240-108">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="57240-109">'ndaki `TypeDef` Kod dosyasında başvurulan belirteç.</span><span class="sxs-lookup"><span data-stu-id="57240-109">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="57240-110">'ndaki Türün özniteliklerini belirten bir bit düzeyinde değer birleşimi.</span><span class="sxs-lookup"><span data-stu-id="57240-110">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57240-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57240-111">Remarks</span></span>  

 <span data-ttu-id="57240-112">`ExportedType`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="57240-112">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57240-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57240-113">Requirements</span></span>  

 <span data-ttu-id="57240-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57240-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57240-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57240-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57240-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="57240-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57240-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57240-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57240-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57240-118">See also</span></span>

- [<span data-ttu-id="57240-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57240-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
