---
title: IMetaDataEmit::DefinePinvokeMap Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6421ca47c3439d94c1ae86caaf2198298872d53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777525"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="3f77c-102">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f77c-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="3f77c-103">Belirtilen belirteç tarafından başvurulan PInvoke imzası özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3f77c-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f77c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f77c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f77c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f77c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="3f77c-106">[in] Hedef yöntemin belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f77c-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="3f77c-107">[in] PInvoke tarafından eşleme yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3f77c-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="3f77c-108">[in] Hedef adı yöntemi yönetilmeyen DLL dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="3f77c-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="3f77c-109">[in] Belirteç hedef için yerel bir DLL.</span><span class="sxs-lookup"><span data-stu-id="3f77c-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f77c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f77c-110">Requirements</span></span>  
 <span data-ttu-id="3f77c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f77c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f77c-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3f77c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f77c-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3f77c-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f77c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f77c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f77c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f77c-115">See also</span></span>

- [<span data-ttu-id="3f77c-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f77c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f77c-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f77c-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
