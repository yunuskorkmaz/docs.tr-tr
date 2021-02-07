---
description: 'Hakkında daha fazla bilgi edinin: _CorImageUnloading Işlevi'
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
ms.openlocfilehash: fe10c97be66aab21793b1ad306aa5d90eaa1ade2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716997"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="a7207-103">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="a7207-103">_CorImageUnloading Function</span></span>

<span data-ttu-id="a7207-104">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="a7207-104">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="a7207-105">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a7207-105">This function is not implemented.</span></span> <span data-ttu-id="a7207-106">Çağrılırsa, E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7207-106">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7207-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7207-107">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7207-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7207-108">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="a7207-109">'ndaki Boşaltılacak görüntünün başlangıç konumuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7207-109">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7207-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7207-110">Requirements</span></span>  

 <span data-ttu-id="a7207-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7207-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7207-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a7207-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7207-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a7207-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7207-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7207-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7207-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7207-115">See also</span></span>

- [<span data-ttu-id="a7207-116">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a7207-116">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
