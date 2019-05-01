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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985809"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="aea22-102">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="aea22-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="aea22-103">Yönetilen modül görüntüleri yüklenmediği zaman yükleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="aea22-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="aea22-104">Bu işlev uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="aea22-104">This function is not implemented.</span></span> <span data-ttu-id="aea22-105">Çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="aea22-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea22-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aea22-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea22-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aea22-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="aea22-108">[in] Görüntüyü kaldırmak için başlangıç konumu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aea22-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea22-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aea22-109">Requirements</span></span>  
 <span data-ttu-id="aea22-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aea22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea22-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="aea22-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aea22-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="aea22-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aea22-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea22-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aea22-114">See also</span></span>

- [<span data-ttu-id="aea22-115">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="aea22-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
