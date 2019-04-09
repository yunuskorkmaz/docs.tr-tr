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
ms.openlocfilehash: 03ce77dd7407db8289abfefba13d71a9af053e10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142057"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="4aae4-102">COR_DEBUG_IL_TO_NATIVE_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="4aae4-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="4aae4-103">Yerel kod için Microsoft Ara dil (MSIL) kodu eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="4aae4-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aae4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4aae4-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="4aae4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4aae4-105">Members</span></span>  
  
|<span data-ttu-id="4aae4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4aae4-106">Member</span></span>|<span data-ttu-id="4aae4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aae4-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="4aae4-108">MSIL kodunun uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="4aae4-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="4aae4-109">Yerel kod başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="4aae4-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="4aae4-110">Yerel kod sonuna uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="4aae4-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4aae4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4aae4-111">Requirements</span></span>  
 <span data-ttu-id="4aae4-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aae4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aae4-113">**Üst bilgi:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="4aae4-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="4aae4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aae4-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4aae4-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4aae4-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4aae4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aae4-116">See also</span></span>

- [<span data-ttu-id="4aae4-117">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4aae4-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="4aae4-118">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4aae4-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="4aae4-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="4aae4-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4aae4-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4aae4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
