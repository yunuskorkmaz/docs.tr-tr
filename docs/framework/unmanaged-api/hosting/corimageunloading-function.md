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
ms.openlocfilehash: 585287f63f57f55e877c94684820833b6d1add60
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616547"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="bf286-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="bf286-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="bf286-103">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="bf286-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="bf286-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="bf286-104">This function is not implemented.</span></span> <span data-ttu-id="bf286-105">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf286-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf286-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bf286-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf286-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf286-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="bf286-108">'ndaki Boşaltılacak görüntünün başlangıç konumuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf286-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf286-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf286-109">Requirements</span></span>  
 <span data-ttu-id="bf286-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf286-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf286-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bf286-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf286-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bf286-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf286-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf286-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf286-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf286-114">See also</span></span>

- [<span data-ttu-id="bf286-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bf286-115">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
