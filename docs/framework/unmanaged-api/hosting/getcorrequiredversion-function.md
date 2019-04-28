---
title: GetCORRequiredVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5786444c36fcfc9547be1db0006757b0a9376c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628112"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="5f6cd-102">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="5f6cd-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="5f6cd-103">Gerekli ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="5f6cd-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f6cd-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f6cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f6cd-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f6cd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f6cd-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="5f6cd-107">[out] Sürüm numarasını belirten bir dize içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5f6cd-108">[in] Arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="5f6cd-109">[out] Arabellekte döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f6cd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f6cd-110">Requirements</span></span>  
 <span data-ttu-id="5f6cd-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f6cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f6cd-112">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f6cd-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f6cd-113">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f6cd-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f6cd-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f6cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f6cd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-115">See also</span></span>

- [<span data-ttu-id="5f6cd-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5f6cd-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
