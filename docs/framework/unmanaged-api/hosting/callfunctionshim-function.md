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
ms.openlocfilehash: 1060ca140db0304c8e5667f7fdf9624b3ac2b64a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429289"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="3e5b9-102">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="3e5b9-102">CallFunctionShim Function</span></span>
<span data-ttu-id="3e5b9-103">Belirtilen ada ve parametreleri belirtilen Kitaplığı'nda sahip işlevine bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="3e5b9-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e5b9-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e5b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e5b9-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="3e5b9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e5b9-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="3e5b9-107">[in] İşlevi içeren kitaplığı adı.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="3e5b9-108">[in] İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="3e5b9-109">[in] İşleve ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="3e5b9-110">[in] İşleve ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="3e5b9-111">[in] İşlevi içeren kitaplığı sürümü.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="3e5b9-112">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-112">[in] Reserved for future use.</span></span> <span data-ttu-id="3e5b9-113">Bu parametrede sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5b9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e5b9-114">Requirements</span></span>  
 <span data-ttu-id="3e5b9-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e5b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e5b9-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e5b9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e5b9-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e5b9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e5b9-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e5b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5b9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e5b9-119">See Also</span></span>  
 [<span data-ttu-id="3e5b9-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3e5b9-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
