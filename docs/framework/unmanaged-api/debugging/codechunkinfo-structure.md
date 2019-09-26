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
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274249"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="02cd3-102">CodeChunkInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="02cd3-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="02cd3-103">Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="02cd3-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02cd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02cd3-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="02cd3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02cd3-105">Members</span></span>  
  
|<span data-ttu-id="02cd3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="02cd3-106">Member</span></span>|<span data-ttu-id="02cd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02cd3-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="02cd3-108">Öbekin başlangıç adresini belirten bir `CORDB_ADDRESS` değer.</span><span class="sxs-lookup"><span data-stu-id="02cd3-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="02cd3-109">Öbekin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="02cd3-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02cd3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02cd3-110">Remarks</span></span>  
 <span data-ttu-id="02cd3-111">Tek kod öbeği, bir işlev gibi bir kod nesnesinin parçası olan yerel kod bölgesidir.</span><span class="sxs-lookup"><span data-stu-id="02cd3-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02cd3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02cd3-112">Requirements</span></span>  
 <span data-ttu-id="02cd3-113">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02cd3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02cd3-114">**Üst bilgi** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="02cd3-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="02cd3-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="02cd3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02cd3-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02cd3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02cd3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02cd3-117">See also</span></span>

- [<span data-ttu-id="02cd3-118">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02cd3-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="02cd3-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="02cd3-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="02cd3-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="02cd3-120">Debugging</span></span>](index.md)
