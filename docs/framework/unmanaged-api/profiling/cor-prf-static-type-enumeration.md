---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_STATIC_TYPE numaralandırması'
title: COR_PRF_STATIC_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: b7171fe4e9c536d94109d46ae6cad9201a15bab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789050"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="b77d5-103">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b77d5-103">COR_PRF_STATIC_TYPE Enumeration</span></span>

<span data-ttu-id="b77d5-104">Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b77d5-104">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="b77d5-105">Bu değerler, alanın birden çok, farklı statik kalitede olduğunu göstermek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b77d5-105">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77d5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b77d5-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b77d5-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b77d5-107">Members</span></span>  
  
|<span data-ttu-id="b77d5-108">Üye</span><span class="sxs-lookup"><span data-stu-id="b77d5-108">Member</span></span>|<span data-ttu-id="b77d5-109">Description</span><span class="sxs-lookup"><span data-stu-id="b77d5-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="b77d5-110">Alan statik değil.</span><span class="sxs-lookup"><span data-stu-id="b77d5-110">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="b77d5-111">Alan, uygulama etki alanı-statik ' dır.</span><span class="sxs-lookup"><span data-stu-id="b77d5-111">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="b77d5-112">Alan, Thread-static ' dir.</span><span class="sxs-lookup"><span data-stu-id="b77d5-112">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="b77d5-113">Alan, bağlam statiktir.</span><span class="sxs-lookup"><span data-stu-id="b77d5-113">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="b77d5-114">Alan göreli sanal adres (RVA)-statik ' dır.</span><span class="sxs-lookup"><span data-stu-id="b77d5-114">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b77d5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b77d5-115">Requirements</span></span>  

 <span data-ttu-id="b77d5-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b77d5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b77d5-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b77d5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b77d5-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b77d5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b77d5-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b77d5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77d5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b77d5-120">See also</span></span>

- [<span data-ttu-id="b77d5-121">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b77d5-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
