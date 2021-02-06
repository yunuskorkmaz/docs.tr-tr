---
description: 'Daha fazla bilgi edinin: COR_PRF_CODE_INFO yapısı'
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
ms.openlocfilehash: 11eae032424a039cac1136c08409b5b4712e6db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649253"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="2c567-103">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="2c567-103">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="2c567-104">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c567-104">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c567-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c567-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2c567-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c567-106">Members</span></span>  
  
|<span data-ttu-id="2c567-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2c567-107">Member</span></span>|<span data-ttu-id="2c567-108">Description</span><span class="sxs-lookup"><span data-stu-id="2c567-108">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="2c567-109">Ardışık kod bloğunun başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="2c567-109">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="2c567-110">Bloğun boyutu.</span><span class="sxs-lookup"><span data-stu-id="2c567-110">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c567-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c567-111">Requirements</span></span>  

 <span data-ttu-id="2c567-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c567-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c567-113">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="2c567-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2c567-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c567-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c567-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c567-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c567-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c567-116">See also</span></span>

- [<span data-ttu-id="2c567-117">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="2c567-117">Profiling Structures</span></span>](profiling-structures.md)
