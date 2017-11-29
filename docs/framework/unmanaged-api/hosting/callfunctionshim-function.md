---
title: "CallFunctionShim İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CallFunctionShim
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CallFunctionShim
helpviewer_keywords: CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e6e2e237887ff273ba73e2568c84d2aaaa38383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="c91ab-102">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="c91ab-102">CallFunctionShim Function</span></span>
<span data-ttu-id="c91ab-103">Belirtilen ada ve parametreleri belirtilen Kitaplığı'nda sahip işlevine bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="c91ab-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="c91ab-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c91ab-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91ab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c91ab-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c91ab-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c91ab-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="c91ab-107">[in] İşlevi içeren kitaplığı adı.</span><span class="sxs-lookup"><span data-stu-id="c91ab-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="c91ab-108">[in] İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="c91ab-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="c91ab-109">[in] İşleve ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="c91ab-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="c91ab-110">[in] İşleve ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="c91ab-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="c91ab-111">[in] İşlevi içeren kitaplığı sürümü.</span><span class="sxs-lookup"><span data-stu-id="c91ab-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c91ab-112">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="c91ab-112">[in] Reserved for future use.</span></span> <span data-ttu-id="c91ab-113">Bu parametrede sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="c91ab-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c91ab-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c91ab-114">Requirements</span></span>  
 <span data-ttu-id="c91ab-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c91ab-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c91ab-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c91ab-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c91ab-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c91ab-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c91ab-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c91ab-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91ab-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c91ab-119">See Also</span></span>  
 [<span data-ttu-id="c91ab-120">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="c91ab-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
