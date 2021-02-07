---
description: ': Imetadatayayma:: SaveToMemory Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b5fbca2c3ce06398de72bf2690108077545fef9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745807"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="7efd1-103">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7efd1-103">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="7efd1-104">Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7efd1-104">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efd1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7efd1-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7efd1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7efd1-106">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="7efd1-107">dışı Meta veri yazmaya başlamak için kullanılacak adres.</span><span class="sxs-lookup"><span data-stu-id="7efd1-107">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7efd1-108">'ndaki Ayrılan belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7efd1-108">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7efd1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7efd1-109">Requirements</span></span>  

 <span data-ttu-id="7efd1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7efd1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efd1-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7efd1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7efd1-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7efd1-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7efd1-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7efd1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efd1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7efd1-114">See also</span></span>

- [<span data-ttu-id="7efd1-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7efd1-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7efd1-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7efd1-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
