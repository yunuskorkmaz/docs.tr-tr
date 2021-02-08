---
description: 'Daha fazla bilgi edinin: CoreClrDebugProcInfo yapısı'
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
ms.openlocfilehash: 04befb057be689e68dd3571a13990da9af64551f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801494"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="01a27-103">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="01a27-103">CoreClrDebugProcInfo Structure</span></span>

<span data-ttu-id="01a27-104">Uzak makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="01a27-104">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a27-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="01a27-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="01a27-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="01a27-106">Members</span></span>  
  
|<span data-ttu-id="01a27-107">Üye</span><span class="sxs-lookup"><span data-stu-id="01a27-107">Member</span></span>|<span data-ttu-id="01a27-108">Description</span><span class="sxs-lookup"><span data-stu-id="01a27-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="01a27-109">İşletim sistemi tarafından atanan işlem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="01a27-109">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="01a27-110">Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="01a27-110">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="01a27-111">Bu tanımlayıcı, işletim sistemi tanımlayıcısından daha az sıklıkta geri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="01a27-111">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="01a27-112">İşlemin komut satırı.</span><span class="sxs-lookup"><span data-stu-id="01a27-112">Command-line of the process.</span></span> <span data-ttu-id="01a27-113">Bu üye kesilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="01a27-113">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01a27-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01a27-114">Requirements</span></span>  

 <span data-ttu-id="01a27-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01a27-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01a27-116">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="01a27-116">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="01a27-117">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="01a27-117">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="01a27-118">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="01a27-118">**.NET Framework Versions:** 3.5 SP1</span></span>
