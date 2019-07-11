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
ms.openlocfilehash: 5a6fd0a9ae798fa5071d9b4b9fac1f8b3c759a20
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750878"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="96e35-102">IMetaDataEmit::SetPinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96e35-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="96e35-103">Ayarlar veya önceki bir çağrı tarafından tanımlandığı şekilde bir yöntemin PInvoke imzası, özelliklerini değiştirir [Imetadataemit::definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="96e35-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96e35-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96e35-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="96e35-106">[in] `mdToken` Hangi eşleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="96e35-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="96e35-107">[in] PInvoke tarafından eşleme yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="96e35-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="96e35-108">Bu, bir bit maskesi, `CorPinvokeMap` değerleri.</span><span class="sxs-lookup"><span data-stu-id="96e35-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="96e35-109">[in] Hedef adı yerel DLL'deki dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="96e35-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="96e35-110">[in] `mdModuleRef` Belirteci için hedef yönetilmeyen DLL.</span><span class="sxs-lookup"><span data-stu-id="96e35-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e35-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96e35-111">Requirements</span></span>  
 <span data-ttu-id="96e35-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e35-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="96e35-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96e35-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="96e35-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96e35-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e35-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96e35-116">See also</span></span>

- [<span data-ttu-id="96e35-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96e35-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="96e35-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96e35-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
