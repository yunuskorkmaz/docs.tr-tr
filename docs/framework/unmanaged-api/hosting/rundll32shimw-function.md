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
ms.openlocfilehash: e661bd82ecf6d804e852cca4a4478084edf303c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141504"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="2bb34-102">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="2bb34-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="2bb34-103">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="2bb34-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="2bb34-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2bb34-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb34-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bb34-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bb34-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bb34-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="2bb34-107">'ndaki Komut çıkışının gösterileceği pencerenin tutamacı.</span><span class="sxs-lookup"><span data-stu-id="2bb34-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="2bb34-108">'ndaki Komutu içeren kitaplığa yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="2bb34-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="2bb34-109">'ndaki Yürütülecek komutu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2bb34-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="2bb34-110">'ndaki Çıkış penceresi için görüntüleme modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2bb34-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb34-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bb34-111">Requirements</span></span>  
 <span data-ttu-id="2bb34-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb34-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb34-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2bb34-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bb34-114">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2bb34-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bb34-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb34-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb34-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb34-116">See also</span></span>

- [<span data-ttu-id="2bb34-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2bb34-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
