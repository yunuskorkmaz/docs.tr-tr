---
description: 'Daha fazla bilgi edinin: CodeChunkInfo yapısı'
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
ms.openlocfilehash: 017a9ee8c608d4efae98eb0a342a3371ef8ec310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712356"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="65f4f-103">CodeChunkInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="65f4f-103">CodeChunkInfo Structure</span></span>

<span data-ttu-id="65f4f-104">Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65f4f-104">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f4f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="65f4f-105">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="65f4f-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="65f4f-106">Members</span></span>  
  
|<span data-ttu-id="65f4f-107">Üye</span><span class="sxs-lookup"><span data-stu-id="65f4f-107">Member</span></span>|<span data-ttu-id="65f4f-108">Description</span><span class="sxs-lookup"><span data-stu-id="65f4f-108">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="65f4f-109">`CORDB_ADDRESS`Öbekin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="65f4f-109">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="65f4f-110">Öbekin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65f4f-110">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65f4f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65f4f-111">Remarks</span></span>  

 <span data-ttu-id="65f4f-112">Tek kod öbeği, bir işlev gibi bir kod nesnesinin parçası olan yerel kod bölgesidir.</span><span class="sxs-lookup"><span data-stu-id="65f4f-112">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f4f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65f4f-113">Requirements</span></span>  

 <span data-ttu-id="65f4f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f4f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f4f-115">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="65f4f-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="65f4f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65f4f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65f4f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f4f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f4f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f4f-118">See also</span></span>

- [<span data-ttu-id="65f4f-119">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65f4f-119">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="65f4f-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="65f4f-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="65f4f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="65f4f-121">Debugging</span></span>](index.md)
