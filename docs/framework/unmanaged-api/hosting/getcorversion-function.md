---
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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617223"
---
# <a name="getcorversion-function"></a><span data-ttu-id="c87c9-102">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c87c9-102">GetCORVersion Function</span></span>
<span data-ttu-id="c87c9-103">Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c87c9-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="c87c9-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c87c9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c87c9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c87c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c87c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c87c9-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="c87c9-107">CLR 'nin şu anda işleme yüklenmiş çalışma zamanının sürümünü belirten bir dize döndürdüğü bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c87c9-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="c87c9-108">Döndürülen dize [CorBindToRuntimeEx](corbindtoruntimeex-function.md)öğesine geçirilen dizelerle aynı formu alır, örneğin, "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="c87c9-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="c87c9-109">Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c87c9-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c87c9-110">`WCHAR`İçinde tutulabilecek karakter sayısı `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="c87c9-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c87c9-111">Aslında ' de döndürülen karakter sayısına yönelik bir işaretçi `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="c87c9-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="c87c9-112">`pbuffer`Null işaretçisiyse, çalışma zamanı E_POINTER döndürür.</span><span class="sxs-lookup"><span data-stu-id="c87c9-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="c87c9-113">Karakter sayısının uzunluğu daha büyükse `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.</span><span class="sxs-lookup"><span data-stu-id="c87c9-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87c9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c87c9-114">Requirements</span></span>  
 <span data-ttu-id="c87c9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87c9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87c9-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c87c9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c87c9-117">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c87c9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c87c9-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87c9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87c9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c87c9-119">See also</span></span>

- [<span data-ttu-id="c87c9-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c87c9-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
