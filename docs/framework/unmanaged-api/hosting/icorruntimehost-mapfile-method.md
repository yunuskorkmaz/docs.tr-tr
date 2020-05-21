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
ms.openlocfilehash: 3b1a0cd9a1dfba6f33a20416f2a10c967f871a06
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762675"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="c3a5e-102">ICorRuntimeHost::MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3a5e-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="c3a5e-103">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="c3a5e-103">Maps the specified file into memory.</span></span> <span data-ttu-id="c3a5e-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c3a5e-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a5e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c3a5e-105">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a5e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3a5e-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="c3a5e-107">'ndaki Eşlenecek dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c3a5e-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="c3a5e-108">dışı Dosyanın eşlenmesinin başlayacağı başlangıç belleği adresi.</span><span class="sxs-lookup"><span data-stu-id="c3a5e-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a5e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3a5e-109">Requirements</span></span>  
 <span data-ttu-id="c3a5e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a5e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a5e-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3a5e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3a5e-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c3a5e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3a5e-113">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c3a5e-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a5e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3a5e-114">See also</span></span>

- [<span data-ttu-id="c3a5e-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3a5e-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
