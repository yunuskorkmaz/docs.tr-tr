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
ms.openlocfilehash: a4dbe090987248ef77ce371b5bc6fb42d898f726
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705416"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="ed277-102">IMetaDataEmit2::SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed277-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>

<span data-ttu-id="ed277-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ed277-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed277-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed277-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed277-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed277-105">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="ed277-106">dışı Meta veri değişim yazmanın başlayacağı adres.</span><span class="sxs-lookup"><span data-stu-id="ed277-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="ed277-107">'ndaki Değişikliklerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ed277-107">[in] The size of the changes.</span></span> <span data-ttu-id="ed277-108">Boyutunu öğrenmek için [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed277-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed277-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed277-109">Requirements</span></span>  

 <span data-ttu-id="ed277-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed277-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed277-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ed277-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed277-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ed277-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed277-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed277-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed277-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed277-114">See also</span></span>

- [<span data-ttu-id="ed277-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed277-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="ed277-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed277-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
