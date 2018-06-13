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
ms.openlocfilehash: 008514e3637a980f3722d0c9896a17be33d54c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431694"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="2a12d-102">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="2a12d-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="2a12d-103">Yükleme dizini işlemine yüklenen ortak dil çalışma zamanı (CLR) döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a12d-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="2a12d-104">Yükleme dizini tam, örneğin, "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="2a12d-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="2a12d-105">Bu işlev kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2a12d-105">This function is deprecated.</span></span> <span data-ttu-id="2a12d-106">Yerine geçen [Iclrruntimeınfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) sağlanan yöntemi [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a12d-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a12d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a12d-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a12d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a12d-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="2a12d-109">[out] Arabellek çalışma zamanı yükleme dizini işlem içine yüklenmiş çalışma zamanı için tam adı içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a12d-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="2a12d-110">Çalışma zamanı işlemine henüz yüklenmedi, işlevi bilgisayarda yüklü çalışma zamanı en son sürümü için uygun dizin bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a12d-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2a12d-111">[in] Bayt olarak boyutu, `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2a12d-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2a12d-112">[out] Döndürülen karakter sayısını `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2a12d-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a12d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a12d-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2a12d-114">Bu işlev, CLR sürüm 4 çalışan işlemleri içinde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2a12d-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="2a12d-115">CLR önceki bir sürümü bilgisayarda yüklüyse, bu işlev bu sürüm için yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a12d-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a12d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a12d-116">Requirements</span></span>  
 <span data-ttu-id="2a12d-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a12d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a12d-118">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2a12d-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a12d-119">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a12d-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a12d-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a12d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a12d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a12d-121">See Also</span></span>  
 [<span data-ttu-id="2a12d-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2a12d-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
