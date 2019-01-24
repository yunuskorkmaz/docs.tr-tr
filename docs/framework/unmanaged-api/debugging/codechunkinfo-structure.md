---
title: Codechunkınfo yapısı1
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
ms.openlocfilehash: d658e360fcfd3fda837c6d7ccab9458594ce9641
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522550"
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="292a7-102">Codechunkınfo yapısı1</span><span class="sxs-lookup"><span data-stu-id="292a7-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="292a7-103">Tek bir öbek kod bellekte temsil eder.</span><span class="sxs-lookup"><span data-stu-id="292a7-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="292a7-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="292a7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="292a7-105">Members</span></span>  
  
|<span data-ttu-id="292a7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="292a7-106">Member</span></span>|<span data-ttu-id="292a7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="292a7-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="292a7-108">A `CORDB_ADDRESS` öbek başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="292a7-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="292a7-109">Baytlarında öbek boyutu.</span><span class="sxs-lookup"><span data-stu-id="292a7-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="292a7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="292a7-110">Remarks</span></span>  
 <span data-ttu-id="292a7-111">Tek parça kodu, bir işlev gibi kod nesnesinin bir parçası olan yerel kod bölgedir.</span><span class="sxs-lookup"><span data-stu-id="292a7-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292a7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="292a7-112">Requirements</span></span>  
 <span data-ttu-id="292a7-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="292a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292a7-114">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="292a7-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="292a7-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="292a7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="292a7-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="292a7-117">See also</span></span>
- [<span data-ttu-id="292a7-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="292a7-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="292a7-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="292a7-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="292a7-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="292a7-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
