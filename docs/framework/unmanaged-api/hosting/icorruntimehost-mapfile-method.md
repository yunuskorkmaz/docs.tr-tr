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
ms.openlocfilehash: b58da58897edbf3ec9492c1f9f1b2f3d7b83e07a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780082"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="ef1ed-102">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef1ed-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="ef1ed-103">Belirtilen dosya belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="ef1ed-103">Maps the specified file into memory.</span></span> <span data-ttu-id="ef1ed-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ef1ed-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef1ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef1ed-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef1ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef1ed-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ef1ed-107">[in] Eşleştirilecek dosya tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="ef1ed-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="ef1ed-108">[out] Başlangıç bellek adresi eşleme dosyası başlanacak.</span><span class="sxs-lookup"><span data-stu-id="ef1ed-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef1ed-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef1ed-109">Requirements</span></span>  
 <span data-ttu-id="ef1ed-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef1ed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef1ed-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef1ed-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef1ed-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ef1ed-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef1ed-113">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ef1ed-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1ed-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef1ed-114">See also</span></span>

- [<span data-ttu-id="ef1ed-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef1ed-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
