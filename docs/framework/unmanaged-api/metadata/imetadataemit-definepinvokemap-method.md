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
ms.openlocfilehash: 447ec44ed3efc4eec84d1e4acd6f2ec1a730bf74
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008033"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="06fc7-102">IMetaDataEmit::DefinePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06fc7-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="06fc7-103">Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06fc7-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fc7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="06fc7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06fc7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06fc7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="06fc7-106">'ndaki Hedef yöntemi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="06fc7-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="06fc7-107">'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="06fc7-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="06fc7-108">'ndaki Yönetilmeyen DLL içindeki hedef dışarı aktarma yönteminin adı.</span><span class="sxs-lookup"><span data-stu-id="06fc7-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="06fc7-109">'ndaki Hedef yerel DLL için belirteç.</span><span class="sxs-lookup"><span data-stu-id="06fc7-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fc7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06fc7-110">Requirements</span></span>  
 <span data-ttu-id="06fc7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06fc7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06fc7-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="06fc7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06fc7-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="06fc7-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06fc7-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06fc7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fc7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06fc7-115">See also</span></span>

- [<span data-ttu-id="06fc7-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06fc7-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="06fc7-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06fc7-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
