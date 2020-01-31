---
title: StackTrace_SimpleContext Yapısı
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: c81a5787eb06971e3d52aff5d1c1154a72564daf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790331"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="138d6-102">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="138d6-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="138d6-103">Tam `CONTEXT` yapısının yerine kullanılabilecek basit bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="138d6-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="138d6-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="138d6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="138d6-105">Members</span></span>  
  
|<span data-ttu-id="138d6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="138d6-106">Member</span></span>|<span data-ttu-id="138d6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="138d6-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="138d6-108">X86 platformlarında yığın işaretçisi veya yığın işaretçisi (ESP) girin.</span><span class="sxs-lookup"><span data-stu-id="138d6-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="138d6-109">Çerçeve kayması veya x86 platformlarında EBP kaydı.</span><span class="sxs-lookup"><span data-stu-id="138d6-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="138d6-110">X86 platformlarında yönerge işaretçisi veya giriş yönergesi işaretçisi (EıP).</span><span class="sxs-lookup"><span data-stu-id="138d6-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="138d6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="138d6-111">Remarks</span></span>  
 <span data-ttu-id="138d6-112">Yığın izleme işlevlerinin genellikle yalnızca adresi, çerçeve sapmasını ve yığın adresini döndürmesi gerektiğinden, büyük bir `CONTEXT` yapısı yerine isteğe bağlı olarak `SimpleContext` yapısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="138d6-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138d6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="138d6-113">Requirements</span></span>  
 <span data-ttu-id="138d6-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="138d6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="138d6-115">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="138d6-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="138d6-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="138d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="138d6-117">See also</span></span>

- [<span data-ttu-id="138d6-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="138d6-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="138d6-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="138d6-119">Debugging</span></span>](index.md)
