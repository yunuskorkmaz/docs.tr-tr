---
title: IMetaDataEmit2::SaveDeltaToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: 8a6f11996425c92d9b0e3123ee2d3a064739454b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492770"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="f8fbd-102">IMetaDataEmit2::SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8fbd-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="f8fbd-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f8fbd-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8fbd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f8fbd-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8fbd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8fbd-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="f8fbd-106">dışı Meta veri değişim yazmanın başlayacağı adres.</span><span class="sxs-lookup"><span data-stu-id="f8fbd-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="f8fbd-107">'ndaki Değişikliklerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f8fbd-107">[in] The size of the changes.</span></span> <span data-ttu-id="f8fbd-108">Boyutunu öğrenmek için [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8fbd-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8fbd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8fbd-109">Requirements</span></span>  
 <span data-ttu-id="f8fbd-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8fbd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8fbd-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f8fbd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8fbd-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f8fbd-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8fbd-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8fbd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fbd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8fbd-114">See also</span></span>

- [<span data-ttu-id="f8fbd-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8fbd-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="f8fbd-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8fbd-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
