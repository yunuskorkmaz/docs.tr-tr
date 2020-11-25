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
ms.openlocfilehash: b64e58a79f3dbe0c91b0c0cefc4a9d918c700cf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718637"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="812ef-102">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="812ef-102">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="812ef-103">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="812ef-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="812ef-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="812ef-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="812ef-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="812ef-105">Members</span></span>  
  
|<span data-ttu-id="812ef-106">Üye</span><span class="sxs-lookup"><span data-stu-id="812ef-106">Member</span></span>|<span data-ttu-id="812ef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="812ef-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="812ef-108">Ardışık kod bloğunun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="812ef-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="812ef-109">Bloğun boyutu.</span><span class="sxs-lookup"><span data-stu-id="812ef-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="812ef-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="812ef-110">Requirements</span></span>  

 <span data-ttu-id="812ef-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="812ef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="812ef-112">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="812ef-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="812ef-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="812ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="812ef-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="812ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="812ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="812ef-115">See also</span></span>

- [<span data-ttu-id="812ef-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="812ef-116">Profiling Structures</span></span>](profiling-structures.md)
