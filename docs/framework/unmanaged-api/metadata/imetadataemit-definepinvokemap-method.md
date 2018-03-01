---
title: "IMetaDataEmit::DefinePinvokeMap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd42c54990fd8aad1b9e6325d59ac7ccc5d6a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="e0d52-102">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d52-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="e0d52-103">Belirtilen belirteç tarafından başvurulan PInvoke imzası özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0d52-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0d52-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0d52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0d52-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e0d52-106">[in] Hedef yöntemin için belirteci.</span><span class="sxs-lookup"><span data-stu-id="e0d52-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="e0d52-107">[in] Eşleme işlemini gerçekleştirmek için PInvoke tarafından kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="e0d52-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="e0d52-108">[in] Yönetilmeyen DLL yönteminde hedef adını verin.</span><span class="sxs-lookup"><span data-stu-id="e0d52-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="e0d52-109">[in] Belirtecin hedefi için yerel DLL'i.</span><span class="sxs-lookup"><span data-stu-id="e0d52-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d52-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0d52-110">Requirements</span></span>  
 <span data-ttu-id="e0d52-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d52-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d52-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0d52-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0d52-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e0d52-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0d52-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d52-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d52-115">See Also</span></span>  
 [<span data-ttu-id="e0d52-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0d52-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e0d52-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0d52-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
