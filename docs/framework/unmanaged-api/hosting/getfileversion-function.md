---
title: GetFileVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d25a3ccdd66ff7acb70f1f5e6c60157b53cc97c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123745"
---
# <a name="getfileversion-function"></a><span data-ttu-id="d6fe5-102">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6fe5-102">GetFileVersion Function</span></span>
<span data-ttu-id="d6fe5-103">Belirtilen arabelleği kullanarak belirtilen dosya, ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="d6fe5-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6fe5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fe5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6fe5-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6fe5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6fe5-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="d6fe5-107">[in] İncelenecek dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="d6fe5-108">[out içinde] Döndürülen sürüm bilgilerini ayrılan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d6fe5-109">[in] Geniş karakter cinsinden boyutu, `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d6fe5-110">[out] Döndürülen bayt cinsinden boyutu `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fe5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6fe5-111">Requirements</span></span>  
 <span data-ttu-id="d6fe5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fe5-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6fe5-113">**Header:** MSCorEE.h</span></span>  
  
 **<span data-ttu-id="d6fe5-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d6fe5-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d6fe5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6fe5-115">See also</span></span>

- [<span data-ttu-id="d6fe5-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6fe5-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
