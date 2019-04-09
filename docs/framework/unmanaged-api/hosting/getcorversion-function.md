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
ms.openlocfilehash: f66e00c3334aecdf8c653f57e28d1b327c4170e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094077"
---
# <a name="getcorversion-function"></a><span data-ttu-id="fc24f-102">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="fc24f-102">GetCORVersion Function</span></span>
<span data-ttu-id="fc24f-103">Geçerli işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc24f-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="fc24f-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc24f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc24f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc24f-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fc24f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc24f-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="fc24f-107">CLR işleme şu anda yüklü olan çalışma zamanı sürümü belirten bir dize döndüren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc24f-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="fc24f-108">Geçirilen dizeler olarak döndürülen dizeyi aynı forma alan [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), örneğin, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="fc24f-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="fc24f-109">Çalışma zamanı işleme henüz yüklenmemiş bir bilgisayarda yüklü olan çalışma zamanı en son sürümü için uygun dizin bilgileri işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc24f-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="fc24f-110">Karakter sayısı (`WCHAR`s), tutulan içinde `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="fc24f-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fc24f-111">Gerçekte döndürülen karakter sayısı için bir işaretçi `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="fc24f-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="fc24f-112">Varsa `pbuffer` null bir işaretçiyse, çalışma zamanı e_poınter döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc24f-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="fc24f-113">Karakter sayısı büyükse, ardından uzunluğunu `pbuffer` , çalışma zamanı ERROR_INSUFFICIENT_BUFFER döndürür.</span><span class="sxs-lookup"><span data-stu-id="fc24f-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc24f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc24f-114">Requirements</span></span>  
 <span data-ttu-id="fc24f-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc24f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc24f-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc24f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc24f-117">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc24f-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fc24f-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fc24f-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc24f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc24f-119">See also</span></span>

- [<span data-ttu-id="fc24f-120">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fc24f-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
