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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178185"
---
# <a name="getcorversion-function"></a><span data-ttu-id="acd26-102">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="acd26-102">GetCORVersion Function</span></span>
<span data-ttu-id="acd26-103">Geçerli işlemde çalışan ortak dil çalışma zamanının (CLR) sürüm numarasını verir.</span><span class="sxs-lookup"><span data-stu-id="acd26-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="acd26-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="acd26-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd26-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acd26-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="acd26-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acd26-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="acd26-107">CLR'nin şu anda işleme yüklenen çalışma zamanının sürümünü belirten bir dize döndürdeği arabelleği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="acd26-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="acd26-108">Döndürülen dize, [CorBindToRuntimeEx'e](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)geçen dizeleri ile aynı şekilde alır, örneğin, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="acd26-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="acd26-109">Çalışma süresi henüz işleme yüklenmediyse, işlev bilgisayarda yüklenen çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="acd26-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="acd26-110">'de `pbuffer`tutulabilen`WCHAR`karakter (ler) sayısı.</span><span class="sxs-lookup"><span data-stu-id="acd26-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="acd26-111">Gerçekte döndürülen `pbuffer`karakter sayısına işaretçi</span><span class="sxs-lookup"><span data-stu-id="acd26-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="acd26-112">Null `pbuffer` işaretçiise, çalışma süresi E_POINTER döndürür.</span><span class="sxs-lookup"><span data-stu-id="acd26-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="acd26-113">Karakter sayısı daha büyükse, `pbuffer` çalışma süresi ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="acd26-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd26-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acd26-114">Requirements</span></span>  
 <span data-ttu-id="acd26-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acd26-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd26-116">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="acd26-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="acd26-117">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="acd26-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acd26-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd26-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd26-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acd26-119">See also</span></span>

- [<span data-ttu-id="acd26-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="acd26-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
