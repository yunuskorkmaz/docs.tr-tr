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
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132393"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="66ac6-102">CodeChunkInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="66ac6-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="66ac6-103">Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="66ac6-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66ac6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66ac6-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="66ac6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="66ac6-105">Members</span></span>  
  
|<span data-ttu-id="66ac6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="66ac6-106">Member</span></span>|<span data-ttu-id="66ac6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66ac6-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="66ac6-108">Öbekin başlangıç adresini belirten bir `CORDB_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="66ac6-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="66ac6-109">Öbekin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="66ac6-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66ac6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66ac6-110">Remarks</span></span>  
 <span data-ttu-id="66ac6-111">Tek kod öbeği, bir işlev gibi bir kod nesnesinin parçası olan yerel kod bölgesidir.</span><span class="sxs-lookup"><span data-stu-id="66ac6-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66ac6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66ac6-112">Requirements</span></span>  
 <span data-ttu-id="66ac6-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66ac6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66ac6-114">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="66ac6-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="66ac6-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66ac6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66ac6-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66ac6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ac6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66ac6-117">See also</span></span>

- [<span data-ttu-id="66ac6-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66ac6-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="66ac6-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="66ac6-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="66ac6-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="66ac6-120">Debugging</span></span>](index.md)
