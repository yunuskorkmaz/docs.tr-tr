---
description: ': ICorRuntimeHost:: MapFile yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 80c01a036de83b32b9d0de745d76bb97825c980b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789638"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="21102-103">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21102-103">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="21102-104">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="21102-104">Maps the specified file into memory.</span></span> <span data-ttu-id="21102-105">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="21102-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21102-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21102-106">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21102-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21102-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="21102-108">'ndaki Eşlenecek dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="21102-108">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="21102-109">dışı Dosyanın eşlenmesinin başlayacağı başlangıç belleği adresi.</span><span class="sxs-lookup"><span data-stu-id="21102-109">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21102-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21102-110">Requirements</span></span>  

 <span data-ttu-id="21102-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21102-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21102-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21102-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21102-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="21102-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21102-114">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="21102-114">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21102-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21102-115">See also</span></span>

- [<span data-ttu-id="21102-116">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21102-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
