---
description: 'Daha fazla bilgi edinin: CallFunctionShim Işlevi'
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
ms.openlocfilehash: 7ddd16a06005011adcf41190929fd62f4132f14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799960"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="80e03-103">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="80e03-103">CallFunctionShim Function</span></span>

<span data-ttu-id="80e03-104">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="80e03-104">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="80e03-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="80e03-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e03-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80e03-106">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e03-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80e03-107">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="80e03-108">'ndaki İşlevi içeren kitaplığın adı.</span><span class="sxs-lookup"><span data-stu-id="80e03-108">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="80e03-109">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="80e03-109">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="80e03-110">'ndaki İşleve geçirilecek ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="80e03-110">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="80e03-111">'ndaki İşleve geçirilecek ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="80e03-111">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="80e03-112">'ndaki İşlevin bulunduğu kitaplığın sürümü.</span><span class="sxs-lookup"><span data-stu-id="80e03-112">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="80e03-113">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="80e03-113">[in] Reserved for future use.</span></span> <span data-ttu-id="80e03-114">Bu parametreye sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="80e03-114">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e03-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80e03-115">Requirements</span></span>  

 <span data-ttu-id="80e03-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e03-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e03-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80e03-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80e03-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80e03-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80e03-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e03-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80e03-120">See also</span></span>

- [<span data-ttu-id="80e03-121">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="80e03-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
