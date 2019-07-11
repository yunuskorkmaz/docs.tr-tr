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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2baefa45deb8c13e8c1e627724fbe271b210a9ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740875"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="6fc88-102">CodeChunkInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6fc88-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="6fc88-103">Tek bir öbek kod bellekte temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6fc88-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fc88-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="6fc88-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6fc88-105">Members</span></span>  
  
|<span data-ttu-id="6fc88-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6fc88-106">Member</span></span>|<span data-ttu-id="6fc88-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fc88-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="6fc88-108">A `CORDB_ADDRESS` öbek başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fc88-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="6fc88-109">Baytlarında öbek boyutu.</span><span class="sxs-lookup"><span data-stu-id="6fc88-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fc88-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fc88-110">Remarks</span></span>  
 <span data-ttu-id="6fc88-111">Tek parça kodu, bir işlev gibi kod nesnesinin bir parçası olan yerel kod bölgedir.</span><span class="sxs-lookup"><span data-stu-id="6fc88-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fc88-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fc88-112">Requirements</span></span>  
 <span data-ttu-id="6fc88-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fc88-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fc88-114">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6fc88-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="6fc88-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fc88-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fc88-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fc88-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc88-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fc88-117">See also</span></span>

- [<span data-ttu-id="6fc88-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6fc88-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="6fc88-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6fc88-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6fc88-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6fc88-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
