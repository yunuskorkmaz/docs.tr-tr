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
ms.openlocfilehash: 9d4ea16a212ac5f0120d63510f07eaee69af739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431480"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="6039c-102">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6039c-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="6039c-103">Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6039c-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6039c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6039c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6039c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6039c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6039c-106">'ndaki Hedef yöntemi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6039c-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="6039c-107">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="6039c-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="6039c-108">'ndaki Yönetilmeyen DLL içindeki hedef dışarı aktarma yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="6039c-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="6039c-109">'ndaki Hedef yerel DLL için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6039c-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6039c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6039c-110">Requirements</span></span>  
 <span data-ttu-id="6039c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6039c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6039c-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6039c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6039c-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6039c-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6039c-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6039c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6039c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6039c-115">See also</span></span>

- [<span data-ttu-id="6039c-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6039c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6039c-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6039c-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
