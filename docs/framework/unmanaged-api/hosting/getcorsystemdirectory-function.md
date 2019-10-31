---
title: GetCORSystemDirectory İşlevi
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 63fb505a92683fda21b6e71a6ca891ca35afba1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136407"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="7066b-102">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="7066b-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="7066b-103">İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7066b-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="7066b-104">Yükleme dizini tam olarak nitelenir, örneğin "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="7066b-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="7066b-105">Bu işlev kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="7066b-105">This function is deprecated.</span></span> <span data-ttu-id="7066b-106">.NET Framework 4 ' te belirtilen [ICLRRuntimeInfo:: GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) yöntemi ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7066b-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7066b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7066b-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="7066b-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7066b-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="7066b-109">dışı Çalışma zamanının, işleme yüklenmiş çalışma zamanı için yükleme dizininin tam adını içeren bir dize döndürdüğü bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7066b-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="7066b-110">Çalışma zamanı işleme henüz yüklenmemişse, işlev, bilgisayarda yüklü olan çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7066b-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7066b-111">'ndaki `pbuffer`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7066b-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7066b-112">dışı `pbuffer`döndürülen karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="7066b-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7066b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7066b-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7066b-114">Bu işlevi CLR sürüm 4 ' ü çalıştıran işlemlerde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7066b-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="7066b-115">Bilgisayarda CLR 'nin önceki bir sürümü yüklüyse, bu işlev söz konusu sürümün yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7066b-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7066b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7066b-116">Requirements</span></span>  
 <span data-ttu-id="7066b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7066b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7066b-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7066b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7066b-119">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7066b-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7066b-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7066b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7066b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7066b-121">See also</span></span>

- [<span data-ttu-id="7066b-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7066b-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
