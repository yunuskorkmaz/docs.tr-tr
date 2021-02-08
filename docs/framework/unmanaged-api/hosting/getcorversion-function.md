---
description: 'Daha fazla bilgi edinin: GetCORVersion Işlevi'
title: GetCORVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 96899b2193be9307314dbc2afb7cd6d70d229cfe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785334"
---
# <a name="getcorversion-function"></a><span data-ttu-id="e5ebb-103">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="e5ebb-103">GetCORVersion Function</span></span>

<span data-ttu-id="e5ebb-104">Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-104">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="e5ebb-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ebb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5ebb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ebb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5ebb-107">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="e5ebb-108">CLR 'nin şu anda işleme yüklenmiş çalışma zamanının sürümünü belirten bir dize döndürdüğü bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-108">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="e5ebb-109">Döndürülen dize [CorBindToRuntimeEx](corbindtoruntimeex-function.md)öğesine geçirilen dizelerle aynı formu alır, örneğin, "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="e5ebb-109">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="e5ebb-110">Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e5ebb-111">`WCHAR`İçinde tutulabilecek karakter sayısı `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="e5ebb-111">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e5ebb-112">Aslında ' de döndürülen karakter sayısına yönelik bir işaretçi `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="e5ebb-112">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="e5ebb-113">`pbuffer`Null işaretçisiyse, çalışma zamanı E_POINTER döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-113">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="e5ebb-114">Karakter sayısının uzunluğu daha büyükse `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-114">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ebb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5ebb-115">Requirements</span></span>  

 <span data-ttu-id="e5ebb-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ebb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ebb-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e5ebb-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5ebb-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5ebb-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5ebb-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ebb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ebb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ebb-120">See also</span></span>

- [<span data-ttu-id="e5ebb-121">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e5ebb-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
