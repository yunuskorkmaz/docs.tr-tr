---
title: RunDll32ShimW İşlevi
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfdf9ffab35f076b85c067c2b412020a5f541b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231090"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="11f56-102">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="11f56-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="11f56-103">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="11f56-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="11f56-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11f56-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f56-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11f56-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f56-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11f56-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="11f56-107">[in] Komut çıktısı görüntülenir bir pencere için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="11f56-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="11f56-108">[in] Komut içeren bir kitaplık için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="11f56-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="11f56-109">[in] Yürütülecek komut belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="11f56-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="11f56-110">[in] Çıkış penceresi için görüntü modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="11f56-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f56-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11f56-111">Requirements</span></span>  
 <span data-ttu-id="11f56-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f56-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11f56-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11f56-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11f56-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11f56-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f56-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f56-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f56-116">See also</span></span>

- [<span data-ttu-id="11f56-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="11f56-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
