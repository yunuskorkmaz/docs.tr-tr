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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9afe4afcaefb9409edb93bd1da96a02db20dbd20
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466760"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="2d2fd-102">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="2d2fd-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="2d2fd-103">İşlem içine yüklenmiş ortak dil çalışma zamanının (CLR) yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="2d2fd-104">Yükleme dizini tam, örneğin, "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="2d2fd-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="2d2fd-105">Bu işlev kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-105">This function is deprecated.</span></span> <span data-ttu-id="2d2fd-106">Yerine geçen [Iclrruntimeınfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) sağlanan yöntemi [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d2fd-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2fd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d2fd-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="2d2fd-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d2fd-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="2d2fd-109">[out] Çalışma zamanı yükleme dizini işleme yüklenecek çalışma zamanı için tam adını içeren bir dize döndüren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="2d2fd-110">Çalışma zamanı işleme henüz yüklenmemiş bir bilgisayarda yüklü olan çalışma zamanı en son sürümü için uygun dizin bilgileri işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2d2fd-111">[in] Bayt cinsinden boyutu, `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2d2fd-112">[out] Döndürülen karakter sayısını `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d2fd-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d2fd-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2d2fd-114">Bu işlev, CLR sürüm 4 çalıştıran işlemlerinde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="2d2fd-115">Bu işlev, CLR'nin önceki bir sürümü bilgisayarda yüklüyse, bu sürüm için yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2fd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d2fd-116">Requirements</span></span>  
 <span data-ttu-id="2d2fd-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d2fd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2fd-118">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d2fd-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d2fd-119">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d2fd-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d2fd-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d2fd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2fd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d2fd-121">See also</span></span>
- [<span data-ttu-id="2d2fd-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2d2fd-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
