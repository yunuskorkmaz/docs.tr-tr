---
title: CallFunctionShim İşlevi
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aeb813cafbf5b18739c4574c386398ac3c7a77b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180485"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="6ddcf-102">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="6ddcf-102">CallFunctionShim Function</span></span>
<span data-ttu-id="6ddcf-103">Belirtilen kitaplık içinde belirtilen ad ve parametreler içeren işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="6ddcf-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ddcf-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ddcf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ddcf-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ddcf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ddcf-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="6ddcf-107">[in] İşlevi içeren kitaplığın adı.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="6ddcf-108">[in] İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="6ddcf-109">[in] İşleve geçirilecek ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="6ddcf-110">[in] İşleve ikinci bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="6ddcf-111">[in] İşlevi içeren kitaplık sürümü.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6ddcf-112">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-112">[in] Reserved for future use.</span></span> <span data-ttu-id="6ddcf-113">Bu parametre sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ddcf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ddcf-114">Requirements</span></span>  
 <span data-ttu-id="6ddcf-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ddcf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ddcf-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ddcf-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ddcf-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ddcf-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6ddcf-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6ddcf-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ddcf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ddcf-119">See also</span></span>

- [<span data-ttu-id="6ddcf-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6ddcf-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
