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
ms.openlocfilehash: 238e59978bd084379fe6c0576107d674812bce8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740789"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="1998e-102">COR_DEBUG_IL_TO_NATIVE_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="1998e-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="1998e-103">Yerel kod için Microsoft Ara dil (MSIL) kodu eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="1998e-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1998e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1998e-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="1998e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1998e-105">Members</span></span>  
  
|<span data-ttu-id="1998e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1998e-106">Member</span></span>|<span data-ttu-id="1998e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1998e-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="1998e-108">MSIL kodunun uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1998e-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="1998e-109">Yerel kod başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1998e-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="1998e-110">Yerel kod sonuna uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1998e-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1998e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1998e-111">Requirements</span></span>  
 <span data-ttu-id="1998e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1998e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1998e-113">**Üst bilgi:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="1998e-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="1998e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1998e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1998e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1998e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1998e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1998e-116">See also</span></span>

- [<span data-ttu-id="1998e-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1998e-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="1998e-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1998e-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="1998e-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1998e-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="1998e-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1998e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
