---
description: 'Daha fazla bilgi edinin: RunDll32ShimW Işlevi'
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
ms.openlocfilehash: d01021358a6cddf15d1a0e1b223c9acff3c64ff7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679504"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="4350b-103">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="4350b-103">RunDll32ShimW Function</span></span>

<span data-ttu-id="4350b-104">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="4350b-104">Executes the specified command.</span></span>  
  
 <span data-ttu-id="4350b-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="4350b-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4350b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4350b-106">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4350b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4350b-107">Parameters</span></span>  

 `hwnd`  
 <span data-ttu-id="4350b-108">'ndaki Komut çıkışının gösterileceği pencerenin tutamacı.</span><span class="sxs-lookup"><span data-stu-id="4350b-108">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="4350b-109">'ndaki Komutu içeren kitaplığa yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="4350b-109">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="4350b-110">'ndaki Yürütülecek komutu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4350b-110">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="4350b-111">'ndaki Çıkış penceresi için görüntüleme modunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4350b-111">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4350b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4350b-112">Requirements</span></span>  

 <span data-ttu-id="4350b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4350b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4350b-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4350b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4350b-115">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4350b-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4350b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4350b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4350b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4350b-117">See also</span></span>

- [<span data-ttu-id="4350b-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4350b-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
