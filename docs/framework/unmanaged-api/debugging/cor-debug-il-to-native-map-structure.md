---
description: 'Daha fazla bilgi edinin: COR_DEBUG_IL_TO_NATIVE_MAP yapısı'
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
ms.openlocfilehash: ec722b86f95e75d4ac00e04e8a602c6b6da64de5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747198"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="31b41-103">COR_DEBUG_IL_TO_NATIVE_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="31b41-103">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>

<span data-ttu-id="31b41-104">Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="31b41-104">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b41-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="31b41-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="31b41-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="31b41-106">Members</span></span>  
  
|<span data-ttu-id="31b41-107">Üye</span><span class="sxs-lookup"><span data-stu-id="31b41-107">Member</span></span>|<span data-ttu-id="31b41-108">Description</span><span class="sxs-lookup"><span data-stu-id="31b41-108">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="31b41-109">MSIL kodunun boşluğu.</span><span class="sxs-lookup"><span data-stu-id="31b41-109">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="31b41-110">Yerel kodun başlangıcının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="31b41-110">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="31b41-111">Yerel kodun sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="31b41-111">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31b41-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31b41-112">Requirements</span></span>  

 <span data-ttu-id="31b41-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31b41-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b41-114">**Üst bilgi:** CorProf. IDL, CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="31b41-114">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="31b41-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31b41-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31b41-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31b41-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b41-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b41-117">See also</span></span>

- [<span data-ttu-id="31b41-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31b41-118">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="31b41-119">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31b41-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="31b41-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="31b41-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="31b41-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="31b41-121">Debugging</span></span>](index.md)
