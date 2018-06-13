---
title: ICorRuntimeHost::MapFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b88758c339cd77bc7e17e0c29969f8783555f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436630"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="60100-102">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60100-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="60100-103">Belirtilen dosya belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="60100-103">Maps the specified file into memory.</span></span> <span data-ttu-id="60100-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="60100-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60100-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60100-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60100-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60100-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="60100-107">[in] Eşleştirilecek dosya tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="60100-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="60100-108">[out] Eşleme dosyasını başlanan başlangıç bellek adresi.</span><span class="sxs-lookup"><span data-stu-id="60100-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60100-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60100-109">Requirements</span></span>  
 <span data-ttu-id="60100-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60100-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60100-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60100-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60100-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="60100-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60100-113">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="60100-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60100-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60100-114">See Also</span></span>  
 [<span data-ttu-id="60100-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60100-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
