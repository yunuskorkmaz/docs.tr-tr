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
ms.openlocfilehash: 92a814d427fcf2e40c7f79e9eb9192e0b7eed4b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132137"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="c2ad8-102">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2ad8-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="c2ad8-103">Uzak makinedeki bir işlemde yüklenen ortak dil çalışma zamanı (CLR) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2ad8-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ad8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2ad8-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="c2ad8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2ad8-105">Members</span></span>  
  
|<span data-ttu-id="c2ad8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c2ad8-106">Member</span></span>|<span data-ttu-id="c2ad8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2ad8-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="c2ad8-108">Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c2ad8-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2ad8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2ad8-109">Requirements</span></span>  
 <span data-ttu-id="c2ad8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ad8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ad8-111">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="c2ad8-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c2ad8-112">**Kitaplık:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="c2ad8-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c2ad8-113">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c2ad8-113">**.NET Framework Versions:** 3.5 SP1</span></span>
