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
ms.openlocfilehash: 1cd5e34d6afefab2fda7e20d4bf73b373ad42787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688607"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="2e244-102">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e244-102">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="2e244-103">Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2e244-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e244-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2e244-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e244-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e244-105">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="2e244-106">dışı Meta veri yazmaya başlamak için kullanılacak adres.</span><span class="sxs-lookup"><span data-stu-id="2e244-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="2e244-107">'ndaki Ayrılan belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2e244-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e244-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e244-108">Requirements</span></span>  

 <span data-ttu-id="2e244-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e244-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e244-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2e244-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e244-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2e244-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e244-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e244-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e244-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e244-113">See also</span></span>

- [<span data-ttu-id="2e244-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e244-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2e244-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e244-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
