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
ms.openlocfilehash: 883f987eb168bf5996baba66f5081875e67f2000
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698732"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="9fc64-102">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="9fc64-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="9fc64-103">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="9fc64-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="9fc64-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fc64-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc64-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fc64-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fc64-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fc64-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="9fc64-107">[in] Komut çıktısı görüntülenir bir pencere için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9fc64-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="9fc64-108">[in] Komut içeren bir kitaplık için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9fc64-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="9fc64-109">[in] Yürütülecek komut belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9fc64-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="9fc64-110">[in] Çıkış penceresi için görüntü modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9fc64-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc64-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fc64-111">Requirements</span></span>  
 <span data-ttu-id="9fc64-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fc64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc64-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fc64-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fc64-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fc64-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fc64-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc64-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fc64-116">See also</span></span>
- [<span data-ttu-id="9fc64-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9fc64-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
