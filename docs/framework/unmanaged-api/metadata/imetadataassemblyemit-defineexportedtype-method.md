---
title: "IMetaDataAssemblyEmit::DefineExportedType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="e1f14-102">IMetaDataAssemblyEmit::DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1f14-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="e1f14-103">Oluşturur bir `ExportedType` belirtilen türü dışarı ve ilişkili meta veri simgesi döndürür için meta verileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="e1f14-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1f14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1f14-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1f14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1f14-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e1f14-106">[in] Dışa aktarılacak türünün adı.</span><span class="sxs-lookup"><span data-stu-id="e1f14-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="e1f14-107">1.1 ortak dil çalışma zamanı sürümü, dışarı aktarılan türünün adı verilen adı tam olarak eşleşmelidir için `TypeDef` türü için.</span><span class="sxs-lookup"><span data-stu-id="e1f14-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="e1f14-108">[in] Burada verilen tür uygulanan belirten bir simge.</span><span class="sxs-lookup"><span data-stu-id="e1f14-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="e1f14-109">İlişkili anlamlarını ve geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e1f14-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="e1f14-110">`mdFile`Bu derleme içinde farklı bir dosya türü uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e1f14-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="e1f14-111">`mdAssemblyRef`Türü farklı bir derlemede uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e1f14-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="e1f14-112">`mdExportedTYpe`Türü, başka bir türü içinde yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="e1f14-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="e1f14-113">`mdFileNil`Türü bildirimi aynı dosyasındaki ve iç içe geçmiş bir tür değil.</span><span class="sxs-lookup"><span data-stu-id="e1f14-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="e1f14-114">[in] Bir belirteç meta verilerinin verilecek türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1f14-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="e1f14-115">Bu değer girildiğini `TypeDef` türü uygulayan ve yalnızca bu dosya bu derlemede olduğunda geçerlidir dosya tablosunda.</span><span class="sxs-lookup"><span data-stu-id="e1f14-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="e1f14-116">[in] Bit düzeyinde bileşimini [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) dışarı aktarılan tür için özellik ayarları tanımlayan numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="e1f14-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="e1f14-117">[out] Dışarı aktarılan türünü gösteren döndürülen meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1f14-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1f14-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1f14-118">Remarks</span></span>  
 <span data-ttu-id="e1f14-119">Bir `ExportedType` meta veri yapısı, bu derlemesi tarafından gösterilir ve bildirim içeren farklı bir modüldeki uygulanan her tür için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1f14-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1f14-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1f14-120">Requirements</span></span>  
 <span data-ttu-id="e1f14-121">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1f14-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1f14-122">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1f14-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1f14-123">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e1f14-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1f14-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1f14-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f14-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f14-125">See Also</span></span>  
 [<span data-ttu-id="e1f14-126">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1f14-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
