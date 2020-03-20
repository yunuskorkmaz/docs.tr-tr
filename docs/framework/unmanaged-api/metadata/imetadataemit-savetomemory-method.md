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
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177575"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="cbbd0-102">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbbd0-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="cbbd0-103">Geçerli kapsamdaki tüm meta verileri belirtilen bellek alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cbbd0-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbbd0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbbd0-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbbd0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbbd0-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="cbbd0-106">[çıkış] Meta veri yazmaya başlanacak adres.</span><span class="sxs-lookup"><span data-stu-id="cbbd0-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="cbbd0-107">[içinde] Ayrılan belleğin boyutu, baytlar içinde.</span><span class="sxs-lookup"><span data-stu-id="cbbd0-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbbd0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbbd0-108">Requirements</span></span>  
 <span data-ttu-id="cbbd0-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbbd0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbbd0-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cbbd0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbbd0-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cbbd0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbbd0-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbbd0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbd0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbbd0-113">See also</span></span>

- [<span data-ttu-id="cbbd0-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbd0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cbbd0-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbbd0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
