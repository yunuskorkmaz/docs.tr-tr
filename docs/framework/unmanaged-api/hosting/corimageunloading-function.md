---
title: _CorImageUnloading İşlevi
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178226"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="1b9e7-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="1b9e7-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="1b9e7-103">Yönetilen modül görüntüleri boşaltıldığında yükleyiciye bilgi verilir.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="1b9e7-104">Bu işlev uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-104">This function is not implemented.</span></span> <span data-ttu-id="1b9e7-105">Çağrılsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9e7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b9e7-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b9e7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b9e7-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="1b9e7-108">[içinde] Boşaltmak için görüntünün başlangıç konumuna bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9e7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b9e7-109">Requirements</span></span>  
 <span data-ttu-id="1b9e7-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9e7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9e7-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b9e7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b9e7-112">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="1b9e7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b9e7-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9e7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9e7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-114">See also</span></span>

- [<span data-ttu-id="1b9e7-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1b9e7-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
