---
title: CodeChunkInfo Yapısı
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 11197246662a93f6a8b57c6e61e49505a9999d00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727438"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="e180e-102">CodeChunkInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="e180e-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="e180e-103">Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e180e-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e180e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e180e-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e180e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e180e-105">Members</span></span>  
  
|<span data-ttu-id="e180e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e180e-106">Member</span></span>|<span data-ttu-id="e180e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e180e-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="e180e-108">`CORDB_ADDRESS`Öbekin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e180e-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="e180e-109">Öbekin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e180e-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e180e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e180e-110">Remarks</span></span>  

 <span data-ttu-id="e180e-111">Tek kod öbeği, bir işlev gibi bir kod nesnesinin parçası olan yerel kod bölgesidir.</span><span class="sxs-lookup"><span data-stu-id="e180e-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e180e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e180e-112">Requirements</span></span>  

 <span data-ttu-id="e180e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e180e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e180e-114">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="e180e-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e180e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e180e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e180e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e180e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e180e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e180e-117">See also</span></span>

- [<span data-ttu-id="e180e-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e180e-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="e180e-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e180e-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e180e-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e180e-120">Debugging</span></span>](index.md)
