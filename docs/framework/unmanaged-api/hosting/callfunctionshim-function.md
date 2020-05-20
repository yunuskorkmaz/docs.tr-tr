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
ms.openlocfilehash: e8945d40a3761ec51a73a8ae90ddc1d84ccab651
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616872"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="6f94e-102">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="6f94e-102">CallFunctionShim Function</span></span>
<span data-ttu-id="6f94e-103">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="6f94e-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="6f94e-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6f94e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f94e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6f94e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6f94e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f94e-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="6f94e-107">'ndaki İşlevi içeren kitaplığın adı.</span><span class="sxs-lookup"><span data-stu-id="6f94e-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="6f94e-108">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="6f94e-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="6f94e-109">'ndaki İşleve geçirilecek ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="6f94e-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="6f94e-110">'ndaki İşleve geçirilecek ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="6f94e-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="6f94e-111">'ndaki İşlevin bulunduğu kitaplığın sürümü.</span><span class="sxs-lookup"><span data-stu-id="6f94e-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6f94e-112">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6f94e-112">[in] Reserved for future use.</span></span> <span data-ttu-id="6f94e-113">Bu parametreye sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="6f94e-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f94e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f94e-114">Requirements</span></span>  
 <span data-ttu-id="6f94e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f94e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f94e-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f94e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f94e-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f94e-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f94e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f94e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f94e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f94e-119">See also</span></span>

- [<span data-ttu-id="6f94e-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6f94e-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
