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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b488b6a887b0c66d8c17f8ea78f48f7d2ea31011
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758399"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="5f30e-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="5f30e-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="5f30e-103">Yönetilen modül görüntüleri yüklenmediği zaman yükleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="5f30e-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="5f30e-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5f30e-104">This function is not implemented.</span></span> <span data-ttu-id="5f30e-105">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f30e-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f30e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f30e-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f30e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f30e-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="5f30e-108">[in] Görüntüyü kaldırmak için başlangıç konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5f30e-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f30e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f30e-109">Requirements</span></span>  
 <span data-ttu-id="5f30e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f30e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f30e-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5f30e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f30e-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5f30e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f30e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f30e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f30e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f30e-114">See also</span></span>

- [<span data-ttu-id="5f30e-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5f30e-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
