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
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210431"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="580e5-102">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="580e5-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="580e5-103">Tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="580e5-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="580e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="580e5-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="580e5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="580e5-105">Members</span></span>  
  
|<span data-ttu-id="580e5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="580e5-106">Member</span></span>|<span data-ttu-id="580e5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="580e5-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="580e5-108">Yığın işaretçisi veya x86 enter yığın işaretçisi (ESP) platformları.</span><span class="sxs-lookup"><span data-stu-id="580e5-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="580e5-109">Çerçeve uzaklığı veya x86 EBP kayıt platformlar.</span><span class="sxs-lookup"><span data-stu-id="580e5-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="580e5-110">Yönerge işaretçisi veya x86 enter yönerge işaretçisi (EIP) platformları.</span><span class="sxs-lookup"><span data-stu-id="580e5-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="580e5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="580e5-111">Remarks</span></span>  
 <span data-ttu-id="580e5-112">Yığın izleme işlevleri genellikle yalnızca adresi, çerçeve uzaklığı ve yığın adresi döndürülecek gerektiğinden, isteğe bağlı olarak kullanabileceğiniz `SimpleContext` yapısı yerine büyük `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="580e5-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="580e5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="580e5-113">Requirements</span></span>  
 <span data-ttu-id="580e5-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="580e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="580e5-115">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="580e5-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="580e5-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="580e5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="580e5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="580e5-117">See also</span></span>

- [<span data-ttu-id="580e5-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="580e5-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="580e5-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="580e5-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
