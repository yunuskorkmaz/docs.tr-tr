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
ms.openlocfilehash: 336fba6defc00eb87fcfa7e6b1aaafa0fcb15691
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494213"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="a818d-102">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="a818d-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="a818d-103">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="a818d-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="a818d-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a818d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a818d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a818d-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a818d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a818d-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="a818d-107">[in] Komut çıktısı görüntülenir bir pencere için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="a818d-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="a818d-108">[in] Komut içeren bir kitaplık için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="a818d-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="a818d-109">[in] Yürütülecek komut belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a818d-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="a818d-110">[in] Çıkış penceresi için görüntü modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a818d-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a818d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a818d-111">Requirements</span></span>  
 <span data-ttu-id="a818d-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a818d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a818d-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a818d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a818d-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a818d-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a818d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a818d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a818d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a818d-116">See also</span></span>
- [<span data-ttu-id="a818d-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a818d-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
