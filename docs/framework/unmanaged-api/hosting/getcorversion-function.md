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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0e922273a7d4e5b98c1321992e5e89e01adb437
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431499"
---
# <a name="getcorversion-function"></a><span data-ttu-id="c0d70-102">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c0d70-102">GetCORVersion Function</span></span>
<span data-ttu-id="c0d70-103">Geçerli işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0d70-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="c0d70-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0d70-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d70-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0d70-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0d70-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0d70-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="c0d70-107">Bir işaretçi bir arabellek için CLR işlemine yüklü çalışma zamanı sürümü belirten bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0d70-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="c0d70-108">Dizeleri geçirilecek şekilde döndürülen dize aynı biçimdedir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), örneğin, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="c0d70-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="c0d70-109">Çalışma zamanı işlemine henüz yüklenmedi, işlevi bilgisayarda yüklü çalışma zamanı en son sürümü için uygun dizin bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0d70-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c0d70-110">Karakter sayısı (`WCHAR`s), tutulan içinde `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="c0d70-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c0d70-111">Gerçekte döndürülen karakter sayısını gösteren bir işaretçi `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="c0d70-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="c0d70-112">Varsa `pbuffer` null işaretçi, çalışma zamanı E_POINTER döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0d70-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="c0d70-113">Karakter sayısını büyükse, ardından uzunluğu `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0d70-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0d70-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0d70-114">Requirements</span></span>  
 <span data-ttu-id="c0d70-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0d70-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0d70-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c0d70-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0d70-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0d70-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0d70-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0d70-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d70-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0d70-119">See Also</span></span>  
 [<span data-ttu-id="c0d70-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c0d70-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
