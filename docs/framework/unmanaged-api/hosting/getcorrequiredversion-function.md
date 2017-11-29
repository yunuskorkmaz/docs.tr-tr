---
title: "GetCORRequiredVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORRequiredVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetCORRequiredVersion
helpviewer_keywords: GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 05267819a1c61c55220f477173069ddf51edaeb4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="a8015-102">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="a8015-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="a8015-103">Gerekli ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="a8015-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="a8015-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8015-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8015-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8015-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8015-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8015-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="a8015-107">[out] Sürüm numarasını belirten bir dize içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a8015-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a8015-108">[in] Arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a8015-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a8015-109">[out] Arabellekte döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a8015-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8015-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8015-110">Requirements</span></span>  
 <span data-ttu-id="a8015-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8015-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8015-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a8015-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8015-113">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8015-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8015-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8015-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8015-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8015-115">See Also</span></span>  
 [<span data-ttu-id="a8015-116">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="a8015-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
