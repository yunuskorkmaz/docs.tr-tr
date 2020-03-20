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
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178199"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="83cf8-102">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="83cf8-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="83cf8-103">İşleme yüklenen ortak dil çalışma zamanının (CLR) yükleme dizini verir.</span><span class="sxs-lookup"><span data-stu-id="83cf8-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="83cf8-104">Yükleme dizini, örneğin "c:\windows\microsoft.net\framework\v1.0.3705" gibi tam niteliklidir.</span><span class="sxs-lookup"><span data-stu-id="83cf8-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="83cf8-105">Bu işlev amortismana hazır.</span><span class="sxs-lookup"><span data-stu-id="83cf8-105">This function is deprecated.</span></span> <span data-ttu-id="83cf8-106">Bu [ICLRRuntimeInfo tarafından yerini::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) yöntemi .NET Framework 4 sağlanan.</span><span class="sxs-lookup"><span data-stu-id="83cf8-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83cf8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83cf8-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="83cf8-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83cf8-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="83cf8-109">[çıkış] Çalışma zamanının, işleme yüklenen çalışma zamanı için yükleme dizininin tam nitelikli adını içeren bir dize döndürdİğİ bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="83cf8-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="83cf8-110">Çalışma süresi henüz işleme yüklenmediyse, işlev bilgisayarda yüklenen çalışma zamanının en son sürümü için uygun dizin bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="83cf8-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="83cf8-111">[içinde] Boyutu, bayt, ve. `pbuffer`</span><span class="sxs-lookup"><span data-stu-id="83cf8-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="83cf8-112">[çıkış] Döndürülen karakter `pbuffer`sayısı.</span><span class="sxs-lookup"><span data-stu-id="83cf8-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83cf8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83cf8-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="83cf8-114">CLR'nin sürüm 4'ü çalıştıran işlemlerde bu işlevi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="83cf8-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="83cf8-115">CLR'nin önceki bir sürümü bilgisayara yüklenmişse, bu işlev bu sürümün yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="83cf8-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83cf8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83cf8-116">Requirements</span></span>  
 <span data-ttu-id="83cf8-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83cf8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83cf8-118">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83cf8-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83cf8-119">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="83cf8-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83cf8-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83cf8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cf8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83cf8-121">See also</span></span>

- [<span data-ttu-id="83cf8-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="83cf8-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
