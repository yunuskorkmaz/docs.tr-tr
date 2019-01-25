---
title: COR_PRF_CODE_INFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83dbb234cf1cacc0e18d4e42bccb427eb54f14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617258"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="d0578-102">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="d0578-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="d0578-103">Yerel kod bellekte bitişik bir bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0578-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0578-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d0578-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d0578-105">Members</span></span>  
  
|<span data-ttu-id="d0578-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d0578-106">Member</span></span>|<span data-ttu-id="d0578-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0578-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="d0578-108">Bitişik kod bloğunu başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="d0578-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="d0578-109">Blok boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0578-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0578-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0578-110">Requirements</span></span>  
 <span data-ttu-id="d0578-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0578-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0578-112">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d0578-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d0578-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0578-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0578-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0578-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0578-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0578-115">See also</span></span>
- [<span data-ttu-id="d0578-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="d0578-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
