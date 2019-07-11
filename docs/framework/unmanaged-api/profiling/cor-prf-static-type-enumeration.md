---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 753c3b38187dd69593dcb0520acef9ce4b137039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751902"
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="fc702-102">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fc702-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="fc702-103">Bir statik alandır ve statik kalite bu durumda, alana uygulanan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc702-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="fc702-104">Bu değerler alan birden çok olduğunu belirtmek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir. farklı bir statik kalitelerini.</span><span class="sxs-lookup"><span data-stu-id="fc702-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc702-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc702-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="fc702-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fc702-106">Members</span></span>  
  
|<span data-ttu-id="fc702-107">Üye</span><span class="sxs-lookup"><span data-stu-id="fc702-107">Member</span></span>|<span data-ttu-id="fc702-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc702-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="fc702-109">Alanı statik değil.</span><span class="sxs-lookup"><span data-stu-id="fc702-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="fc702-110">Uygulama etki alanı statik alandır.</span><span class="sxs-lookup"><span data-stu-id="fc702-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="fc702-111">İş parçacığı statik alandır.</span><span class="sxs-lookup"><span data-stu-id="fc702-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="fc702-112">Bağlam statik alandır.</span><span class="sxs-lookup"><span data-stu-id="fc702-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="fc702-113">Göreli sanal adres (RVA) alandır-statik.</span><span class="sxs-lookup"><span data-stu-id="fc702-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc702-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc702-114">Requirements</span></span>  
 <span data-ttu-id="fc702-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc702-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc702-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc702-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc702-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc702-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc702-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc702-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc702-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc702-119">See also</span></span>

- [<span data-ttu-id="fc702-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fc702-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
