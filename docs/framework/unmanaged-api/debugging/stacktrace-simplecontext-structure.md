---
description: 'Daha fazla bilgi edinin: StackTrace_SimpleContext yapısı'
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
ms.openlocfilehash: 22a0acada5ef2d392dfdef5326953be137280d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800571"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="2ea47-103">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="2ea47-103">StackTrace_SimpleContext Structure</span></span>

<span data-ttu-id="2ea47-104">Tam bir yapının yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="2ea47-104">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea47-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ea47-105">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="2ea47-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2ea47-106">Members</span></span>  
  
|<span data-ttu-id="2ea47-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2ea47-107">Member</span></span>|<span data-ttu-id="2ea47-108">Description</span><span class="sxs-lookup"><span data-stu-id="2ea47-108">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="2ea47-109">X86 platformlarında yığın işaretçisi veya yığın işaretçisi (ESP) girin.</span><span class="sxs-lookup"><span data-stu-id="2ea47-109">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="2ea47-110">Çerçeve kayması veya x86 platformlarında EBP kaydı.</span><span class="sxs-lookup"><span data-stu-id="2ea47-110">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="2ea47-111">X86 platformlarında yönerge işaretçisi veya giriş yönergesi işaretçisi (EıP).</span><span class="sxs-lookup"><span data-stu-id="2ea47-111">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ea47-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ea47-112">Remarks</span></span>  

 <span data-ttu-id="2ea47-113">Yığın izleme işlevlerinin tipik olarak yalnızca adresi, çerçeve sapmasını ve yığın adresini döndürmesi gerektiğinden, `SimpleContext` büyük bir yapı yerine isteğe bağlı olarak yapıyı kullanabilirsiniz `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="2ea47-113">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea47-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ea47-114">Requirements</span></span>  

 <span data-ttu-id="2ea47-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ea47-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ea47-116">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="2ea47-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="2ea47-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ea47-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea47-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea47-118">See also</span></span>

- [<span data-ttu-id="2ea47-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="2ea47-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2ea47-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2ea47-120">Debugging</span></span>](index.md)
