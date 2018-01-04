---
title: "Codechunkınfo Structure1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CodeChunkInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: CodeChunkInfo
helpviewer_keywords: CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7b3b858d645f01f58ba0b67465b22dd05282656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="313d4-102">Codechunkınfo Structure1</span><span class="sxs-lookup"><span data-stu-id="313d4-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="313d4-103">Tek bir Öbek bellek kod temsil eder.</span><span class="sxs-lookup"><span data-stu-id="313d4-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="313d4-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="313d4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="313d4-105">Members</span></span>  
  
|<span data-ttu-id="313d4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="313d4-106">Member</span></span>|<span data-ttu-id="313d4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="313d4-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="313d4-108">A `CORDB_ADDRESS` öbek başlangıç adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="313d4-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="313d4-109">Baytını öbek boyutu.</span><span class="sxs-lookup"><span data-stu-id="313d4-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="313d4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="313d4-110">Remarks</span></span>  
 <span data-ttu-id="313d4-111">Tek öbek kod, bir işlev gibi kod nesnesinin bir parçası olan yerel kod bölgedir.</span><span class="sxs-lookup"><span data-stu-id="313d4-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="313d4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="313d4-112">Requirements</span></span>  
 <span data-ttu-id="313d4-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="313d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="313d4-114">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="313d4-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="313d4-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="313d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="313d4-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="313d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="313d4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="313d4-117">See Also</span></span>  
 [<span data-ttu-id="313d4-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="313d4-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="313d4-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="313d4-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="313d4-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="313d4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
