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
ms.openlocfilehash: b772de720a8c3b669bd3cbe9591637d931cb8763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430625"
---
# <a name="getfileversion-function"></a><span data-ttu-id="4cb26-102">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="4cb26-102">GetFileVersion Function</span></span>
<span data-ttu-id="4cb26-103">Belirtilen arabellek kullanarak dosyanın belirtilen ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="4cb26-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="4cb26-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4cb26-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb26-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cb26-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cb26-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cb26-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="4cb26-107">[in] İncelenmesi için dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="4cb26-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="4cb26-108">[içinde out] Döndürülen sürüm bilgilerini ayrılan arabellek.</span><span class="sxs-lookup"><span data-stu-id="4cb26-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4cb26-109">[in] Geniş karakterler boyutu, `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4cb26-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="4cb26-110">[out] Dönen bayt cinsinden boyutu `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4cb26-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb26-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cb26-111">Requirements</span></span>  
 <span data-ttu-id="4cb26-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cb26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb26-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cb26-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cb26-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb26-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb26-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4cb26-115">See Also</span></span>  
 [<span data-ttu-id="4cb26-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4cb26-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
