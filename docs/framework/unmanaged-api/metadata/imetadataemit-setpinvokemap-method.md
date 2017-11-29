---
title: "IMetaDataEmit::SetPinvokeMap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="4c9e4-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c9e4-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="4c9e4-103">Ayarlar veya önceki bir çağrı tarafından tanımlandığı şekilde bir yöntemin PInvoke imzası özelliklerini değiştirir [Imetadataemit::definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c9e4-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c9e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c9e4-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c9e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c9e4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4c9e4-106">[in] `mdToken` Bilgiler hangi eşleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="4c9e4-107">[in] Eşleme işlemini gerçekleştirmek için PInvoke tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="4c9e4-108">Bu, bir bit maskesi olan `CorPinvokeMap` değerleri.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="4c9e4-109">[in] Yerel DLL'i hedef dışa aktarmanın adı.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="4c9e4-110">[in] `mdModuleRef` Hedefi için belirteç yönetilmeyen DLL.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9e4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c9e4-111">Requirements</span></span>  
 <span data-ttu-id="4c9e4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9e4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9e4-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c9e4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c9e4-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4c9e4-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c9e4-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9e4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9e4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-116">See Also</span></span>  
 [<span data-ttu-id="4c9e4-117">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c9e4-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4c9e4-118">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c9e4-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
