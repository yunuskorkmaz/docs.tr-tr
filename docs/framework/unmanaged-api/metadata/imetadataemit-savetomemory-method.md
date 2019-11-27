---
title: IMetaDataEmit::SaveToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: be4fb0b4b49408a97b318e0f54f5a753f3f24ef1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435801"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="cb943-102">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb943-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="cb943-103">Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cb943-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb943-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb943-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb943-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb943-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="cb943-106">dışı Meta veri yazmaya başlamak için kullanılacak adres.</span><span class="sxs-lookup"><span data-stu-id="cb943-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="cb943-107">'ndaki Ayrılan belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cb943-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb943-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb943-108">Requirements</span></span>  
 <span data-ttu-id="cb943-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb943-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb943-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb943-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb943-111">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cb943-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb943-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb943-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb943-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb943-113">See also</span></span>

- [<span data-ttu-id="cb943-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb943-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cb943-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb943-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
