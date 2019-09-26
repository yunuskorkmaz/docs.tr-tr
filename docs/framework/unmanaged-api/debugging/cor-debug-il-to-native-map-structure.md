---
title: COR_DEBUG_IL_TO_NATIVE_MAP Yapısı
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274069"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="577c2-102">COR_DEBUG_IL_TO_NATIVE_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="577c2-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="577c2-103">Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="577c2-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="577c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="577c2-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="577c2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="577c2-105">Members</span></span>  
  
|<span data-ttu-id="577c2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="577c2-106">Member</span></span>|<span data-ttu-id="577c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="577c2-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="577c2-108">MSIL kodunun boşluğu.</span><span class="sxs-lookup"><span data-stu-id="577c2-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="577c2-109">Yerel kodun başlangıcının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="577c2-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="577c2-110">Yerel kodun sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="577c2-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="577c2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="577c2-111">Requirements</span></span>  
 <span data-ttu-id="577c2-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="577c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="577c2-113">**Üst bilgi** CorProf. IDL, CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="577c2-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="577c2-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="577c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="577c2-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="577c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577c2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="577c2-116">See also</span></span>

- [<span data-ttu-id="577c2-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="577c2-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="577c2-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="577c2-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="577c2-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="577c2-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="577c2-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="577c2-120">Debugging</span></span>](index.md)
