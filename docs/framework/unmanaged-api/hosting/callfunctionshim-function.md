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
ms.openlocfilehash: d39e15a2ba71ba0c0147482259f5618dcb5d298b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192102"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="30df5-102">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="30df5-102">CallFunctionShim Function</span></span>
<span data-ttu-id="30df5-103">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="30df5-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="30df5-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="30df5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30df5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30df5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="30df5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30df5-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="30df5-107">'ndaki İşlevi içeren kitaplığın adı.</span><span class="sxs-lookup"><span data-stu-id="30df5-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="30df5-108">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="30df5-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="30df5-109">'ndaki İşleve geçirilecek ilk bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="30df5-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="30df5-110">'ndaki İşleve geçirilecek ikinci bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="30df5-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="30df5-111">'ndaki İşlevin bulunduğu kitaplığın sürümü.</span><span class="sxs-lookup"><span data-stu-id="30df5-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="30df5-112">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="30df5-112">[in] Reserved for future use.</span></span> <span data-ttu-id="30df5-113">Bu parametreye sıfır geçirin.</span><span class="sxs-lookup"><span data-stu-id="30df5-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30df5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30df5-114">Requirements</span></span>  
 <span data-ttu-id="30df5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30df5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30df5-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30df5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30df5-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="30df5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30df5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30df5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30df5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30df5-119">See also</span></span>

- [<span data-ttu-id="30df5-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="30df5-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
