---
title: "RunDll32ShimW İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a046ed8d540b27bfb73a6e94f148d41f8ac7b264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="bc0b0-102">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="bc0b0-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="bc0b0-103">Belirtilen komut yürütür.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="bc0b0-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc0b0-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0b0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc0b0-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc0b0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc0b0-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="bc0b0-107">[in] Komut çıktısı görüntülenir bir pencere için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="bc0b0-108">[in] Komutu içeren kitaplığı için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="bc0b0-109">[in] Yürütülecek komut belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="bc0b0-110">[in] Çıktı penceresi görüntü modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0b0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc0b0-111">Requirements</span></span>  
 <span data-ttu-id="bc0b0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc0b0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc0b0-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc0b0-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc0b0-114">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc0b0-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc0b0-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc0b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0b0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc0b0-116">See Also</span></span>  
 [<span data-ttu-id="bc0b0-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bc0b0-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
