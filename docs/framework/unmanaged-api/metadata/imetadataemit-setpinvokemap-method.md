---
title: IMetaDataEmit::SetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ed2c818ce9e11ff6eca26ac1c6f13b19668551b7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485336"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="65e42-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65e42-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="65e42-103">Ayarlar veya önceki bir çağrı tarafından tanımlandığı şekilde bir yöntemin PInvoke imzası, özelliklerini değiştirir [Imetadataemit::definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="65e42-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65e42-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65e42-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65e42-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="65e42-106">[in] `mdToken` Hangi eşleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="65e42-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="65e42-107">[in] PInvoke tarafından eşleme yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="65e42-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="65e42-108">Bu, bir bit maskesi, `CorPinvokeMap` değerleri.</span><span class="sxs-lookup"><span data-stu-id="65e42-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="65e42-109">[in] Hedef adı yerel DLL'deki dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="65e42-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="65e42-110">[in] `mdModuleRef` Belirteci için hedef yönetilmeyen DLL.</span><span class="sxs-lookup"><span data-stu-id="65e42-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e42-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65e42-111">Requirements</span></span>  
 <span data-ttu-id="65e42-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e42-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65e42-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65e42-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="65e42-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65e42-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e42-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65e42-116">See also</span></span>
- [<span data-ttu-id="65e42-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65e42-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="65e42-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65e42-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
