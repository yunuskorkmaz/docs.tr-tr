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
ms.openlocfilehash: 60e1d5d49f6f8c6fec060d8751e94410986aa3fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671388"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="5972f-102">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5972f-102">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="5972f-103">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="5972f-103">Maps the specified file into memory.</span></span> <span data-ttu-id="5972f-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5972f-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5972f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5972f-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5972f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5972f-106">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="5972f-107">'ndaki Eşlenecek dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="5972f-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="5972f-108">dışı Dosyanın eşlenmesinin başlayacağı başlangıç belleği adresi.</span><span class="sxs-lookup"><span data-stu-id="5972f-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5972f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5972f-109">Requirements</span></span>  

 <span data-ttu-id="5972f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5972f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5972f-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5972f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5972f-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5972f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5972f-113">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5972f-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5972f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5972f-114">See also</span></span>

- [<span data-ttu-id="5972f-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5972f-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
