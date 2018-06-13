---
title: Codechunkınfo Structure1
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
ms.openlocfilehash: 6e3d138700ef06da7b40a88a768a41f3ffcb38eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403246"
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="17452-102">Codechunkınfo Structure1</span><span class="sxs-lookup"><span data-stu-id="17452-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="17452-103">Tek bir Öbek bellek kod temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17452-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17452-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17452-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="17452-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="17452-105">Members</span></span>  
  
|<span data-ttu-id="17452-106">Üye</span><span class="sxs-lookup"><span data-stu-id="17452-106">Member</span></span>|<span data-ttu-id="17452-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17452-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="17452-108">A `CORDB_ADDRESS` öbek başlangıç adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="17452-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="17452-109">Baytını öbek boyutu.</span><span class="sxs-lookup"><span data-stu-id="17452-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17452-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17452-110">Remarks</span></span>  
 <span data-ttu-id="17452-111">Tek öbek kod, bir işlev gibi kod nesnesinin bir parçası olan yerel kod bölgedir.</span><span class="sxs-lookup"><span data-stu-id="17452-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17452-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17452-112">Requirements</span></span>  
 <span data-ttu-id="17452-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17452-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17452-114">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="17452-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="17452-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17452-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17452-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17452-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17452-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17452-117">See Also</span></span>  
 [<span data-ttu-id="17452-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17452-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="17452-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="17452-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="17452-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="17452-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
