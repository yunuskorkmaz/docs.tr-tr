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
ms.openlocfilehash: bcf1b49f0576f5dbd73c001f8edff7a9ab29af22
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139513"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="cc1eb-102">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc1eb-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="cc1eb-103">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-103">Maps the specified file into memory.</span></span> <span data-ttu-id="cc1eb-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc1eb-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc1eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc1eb-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="cc1eb-107">'ndaki Eşlenecek dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="cc1eb-108">dışı Dosyanın eşlenmesinin başlayacağı başlangıç belleği adresi.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc1eb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc1eb-109">Requirements</span></span>  
 <span data-ttu-id="cc1eb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc1eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc1eb-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc1eb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc1eb-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cc1eb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc1eb-113">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="cc1eb-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc1eb-114">See also</span></span>

- [<span data-ttu-id="cc1eb-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc1eb-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
