---
title: CoreClrDebugProcInfo Yapısı
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fc34add4038d25d60e4728847e0d84914a14e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739422"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="1fa08-102">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="1fa08-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="1fa08-103">Uzak bir makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1fa08-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fa08-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="1fa08-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1fa08-105">Members</span></span>  
  
|<span data-ttu-id="1fa08-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1fa08-106">Member</span></span>|<span data-ttu-id="1fa08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fa08-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="1fa08-108">İşletim sistemi tarafından atanan işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1fa08-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="1fa08-109">Hedef makine üzerinde çalışan uzaktan hata ayıklama proxy'si tarafından atanan işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1fa08-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="1fa08-110">Bu tanımlayıcı işletim sistemi tanımlayıcısı daha az sıklıkta geri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1fa08-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="1fa08-111">İşlemin komut satırı.</span><span class="sxs-lookup"><span data-stu-id="1fa08-111">Command-line of the process.</span></span> <span data-ttu-id="1fa08-112">Bu üye kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="1fa08-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fa08-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fa08-113">Requirements</span></span>  
 <span data-ttu-id="1fa08-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fa08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa08-115">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="1fa08-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="1fa08-116">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="1fa08-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="1fa08-117">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1fa08-117">**.NET Framework Versions:** 3.5 SP1</span></span>
