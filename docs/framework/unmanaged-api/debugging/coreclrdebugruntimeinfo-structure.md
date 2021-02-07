---
description: 'Daha fazla bilgi edinin: CoreCLR[gruntimeınfo yapısı'
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
ms.openlocfilehash: 588e8bd1598996d1676e2df5517bd9a52eb59df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661720"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="015ac-103">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="015ac-103">CoreClrDebugRuntimeInfo Structure</span></span>

<span data-ttu-id="015ac-104">Uzak makinedeki bir işlemde yüklenen ortak dil çalışma zamanı (CLR) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="015ac-104">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="015ac-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="015ac-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="015ac-106">Members</span></span>  
  
|<span data-ttu-id="015ac-107">Üye</span><span class="sxs-lookup"><span data-stu-id="015ac-107">Member</span></span>|<span data-ttu-id="015ac-108">Description</span><span class="sxs-lookup"><span data-stu-id="015ac-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="015ac-109">Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="015ac-109">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="015ac-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="015ac-110">Requirements</span></span>  

 <span data-ttu-id="015ac-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015ac-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="015ac-112">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="015ac-112">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="015ac-113">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="015ac-113">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="015ac-114">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="015ac-114">**.NET Framework Versions:** 3.5 SP1</span></span>
