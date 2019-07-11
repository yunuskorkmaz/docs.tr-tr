---
title: CoreClrDebugRuntimeInfo Yapısı
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b58832e110f67a54d3bd57a7284b2e26e43d6bf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739410"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="92835-102">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="92835-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="92835-103">Bir işlem uzak bir makinede yüklü olduğu bir ortak dil çalışma zamanı (CLR) örneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="92835-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92835-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92835-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="92835-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="92835-105">Members</span></span>  
  
|<span data-ttu-id="92835-106">Üye</span><span class="sxs-lookup"><span data-stu-id="92835-106">Member</span></span>|<span data-ttu-id="92835-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92835-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="92835-108">Hedef makine üzerinde çalışan uzaktan hata ayıklama proxy'si tarafından atanan çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="92835-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92835-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92835-109">Requirements</span></span>  
 <span data-ttu-id="92835-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92835-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92835-111">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="92835-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="92835-112">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="92835-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="92835-113">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="92835-113">**.NET Framework Versions:** 3.5 SP1</span></span>
