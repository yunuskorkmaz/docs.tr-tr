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
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966048"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="f0e39-102">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="f0e39-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="f0e39-103">Bir işlem uzak bir makinede yüklü olduğu bir ortak dil çalışma zamanı (CLR) örneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0e39-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0e39-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="f0e39-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f0e39-105">Members</span></span>  
  
|<span data-ttu-id="f0e39-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f0e39-106">Member</span></span>|<span data-ttu-id="f0e39-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0e39-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="f0e39-108">Hedef makine üzerinde çalışan uzaktan hata ayıklama proxy'si tarafından atanan çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0e39-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0e39-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0e39-109">Requirements</span></span>  
 <span data-ttu-id="f0e39-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e39-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e39-111">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="f0e39-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f0e39-112">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f0e39-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f0e39-113">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f0e39-113">**.NET Framework Versions:** 3.5 SP1</span></span>
