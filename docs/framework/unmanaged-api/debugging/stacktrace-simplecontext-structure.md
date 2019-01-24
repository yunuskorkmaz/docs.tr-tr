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
ms.openlocfilehash: 510ef77f217cdd6e3441e3d6684d431fc31307fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698927"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="19b43-102">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="19b43-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="19b43-103">Tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="19b43-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19b43-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="19b43-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="19b43-105">Members</span></span>  
  
|<span data-ttu-id="19b43-106">Üye</span><span class="sxs-lookup"><span data-stu-id="19b43-106">Member</span></span>|<span data-ttu-id="19b43-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19b43-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="19b43-108">Yığın işaretçisi veya x86 enter yığın işaretçisi (ESP) platformları.</span><span class="sxs-lookup"><span data-stu-id="19b43-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="19b43-109">Çerçeve uzaklığı veya x86 EBP kayıt platformlar.</span><span class="sxs-lookup"><span data-stu-id="19b43-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="19b43-110">Yönerge işaretçisi veya x86 enter yönerge işaretçisi (EIP) platformları.</span><span class="sxs-lookup"><span data-stu-id="19b43-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19b43-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19b43-111">Remarks</span></span>  
 <span data-ttu-id="19b43-112">Yığın izleme işlevleri genellikle yalnızca adresi, çerçeve uzaklığı ve yığın adresi döndürülecek gerektiğinden, isteğe bağlı olarak kullanabileceğiniz `SimpleContext` yapısı yerine büyük `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="19b43-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19b43-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19b43-113">Requirements</span></span>  
 <span data-ttu-id="19b43-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19b43-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19b43-115">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="19b43-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="19b43-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19b43-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b43-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19b43-117">See also</span></span>
- [<span data-ttu-id="19b43-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="19b43-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="19b43-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="19b43-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
