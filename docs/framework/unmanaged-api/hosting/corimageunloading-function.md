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
ms.openlocfilehash: a8326f95286ef05dd370797a531417f81ed5c65b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723161"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="f9240-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="f9240-102">_CorImageUnloading Function</span></span>

<span data-ttu-id="f9240-103">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="f9240-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="f9240-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f9240-104">This function is not implemented.</span></span> <span data-ttu-id="f9240-105">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9240-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9240-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9240-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9240-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9240-107">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="f9240-108">'ndaki Boşaltılacak görüntünün başlangıç konumuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9240-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9240-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9240-109">Requirements</span></span>  

 <span data-ttu-id="f9240-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9240-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9240-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9240-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9240-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f9240-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9240-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9240-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9240-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9240-114">See also</span></span>

- [<span data-ttu-id="f9240-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f9240-115">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
