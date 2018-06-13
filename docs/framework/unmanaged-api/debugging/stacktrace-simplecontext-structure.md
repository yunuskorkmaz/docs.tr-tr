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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf2ba752ace49ae288857dc22819a8e7e429a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424059"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="f54ca-102">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="f54ca-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="f54ca-103">Tam yerine kullanılabilir basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="f54ca-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f54ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f54ca-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="f54ca-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f54ca-105">Members</span></span>  
  
|<span data-ttu-id="f54ca-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f54ca-106">Member</span></span>|<span data-ttu-id="f54ca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f54ca-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="f54ca-108">Yığın işaretçisi veya x86 enter yığın işaretçisi (ESP) platformlar.</span><span class="sxs-lookup"><span data-stu-id="f54ca-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="f54ca-109">Çerçeve uzaklık ya da x86 EBP kasayla platformlar.</span><span class="sxs-lookup"><span data-stu-id="f54ca-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="f54ca-110">Yönerge işaretçisi veya x86 enter yönerge işaretçisi (EIP) platformlar.</span><span class="sxs-lookup"><span data-stu-id="f54ca-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f54ca-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f54ca-111">Remarks</span></span>  
 <span data-ttu-id="f54ca-112">Yığın izleme işlevleri genellikle yalnızca adresini, çerçeve uzaklık ve yığın adresini döndürülecek gerektiğinden, isteğe bağlı olarak kullanabileceğiniz `SimpleContext` büyük yerine yapısı `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="f54ca-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f54ca-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f54ca-113">Requirements</span></span>  
 <span data-ttu-id="f54ca-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f54ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f54ca-115">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="f54ca-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="f54ca-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f54ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54ca-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f54ca-117">See Also</span></span>  
 [<span data-ttu-id="f54ca-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="f54ca-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="f54ca-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f54ca-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
