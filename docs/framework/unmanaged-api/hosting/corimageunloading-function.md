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
ms.openlocfilehash: 1cb5f9decbcdfb71f67a5132dc59773f1de8b0a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086435"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="38155-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="38155-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="38155-103">Yönetilen modül görüntüleri yüklenmediği zaman yükleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="38155-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="38155-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="38155-104">This function is not implemented.</span></span> <span data-ttu-id="38155-105">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="38155-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38155-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38155-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38155-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38155-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="38155-108">[in] Görüntüyü kaldırmak için başlangıç konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38155-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38155-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38155-109">Requirements</span></span>  
 <span data-ttu-id="38155-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38155-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38155-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="38155-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38155-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="38155-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="38155-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="38155-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38155-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38155-114">See also</span></span>

- [<span data-ttu-id="38155-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="38155-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
