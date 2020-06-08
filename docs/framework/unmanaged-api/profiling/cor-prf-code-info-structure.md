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
ms.openlocfilehash: 9dbe0219f5932a9d212edaf5181b96335c47db0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501020"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="6c6df-102">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c6df-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="6c6df-103">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c6df-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c6df-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="6c6df-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6c6df-105">Members</span></span>  
  
|<span data-ttu-id="6c6df-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6c6df-106">Member</span></span>|<span data-ttu-id="6c6df-107">Description</span><span class="sxs-lookup"><span data-stu-id="6c6df-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="6c6df-108">Ardışık kod bloğunun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="6c6df-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="6c6df-109">Bloğun boyutu.</span><span class="sxs-lookup"><span data-stu-id="6c6df-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c6df-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c6df-110">Requirements</span></span>  
 <span data-ttu-id="6c6df-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6df-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6df-112">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="6c6df-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6c6df-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c6df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c6df-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6df-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c6df-115">See also</span></span>

- [<span data-ttu-id="6c6df-116">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="6c6df-116">Profiling Structures</span></span>](profiling-structures.md)
