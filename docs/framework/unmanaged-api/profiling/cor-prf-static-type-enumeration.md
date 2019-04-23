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
ms.openlocfilehash: 310915ce84819a2a5a2d5e1f22356b61c16e7ec7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190502"
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="208ea-102">COR_PRF_STATIC_TYPE Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="208ea-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="208ea-103">Bir statik alandır ve statik kalite bu durumda, alana uygulanan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="208ea-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="208ea-104">Bu değerler alan birden çok olduğunu belirtmek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir. farklı bir statik kalitelerini.</span><span class="sxs-lookup"><span data-stu-id="208ea-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208ea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="208ea-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="208ea-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="208ea-106">Members</span></span>  
  
|<span data-ttu-id="208ea-107">Üye</span><span class="sxs-lookup"><span data-stu-id="208ea-107">Member</span></span>|<span data-ttu-id="208ea-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="208ea-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="208ea-109">Alanı statik değil.</span><span class="sxs-lookup"><span data-stu-id="208ea-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="208ea-110">Uygulama etki alanı statik alandır.</span><span class="sxs-lookup"><span data-stu-id="208ea-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="208ea-111">İş parçacığı statik alandır.</span><span class="sxs-lookup"><span data-stu-id="208ea-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="208ea-112">Bağlam statik alandır.</span><span class="sxs-lookup"><span data-stu-id="208ea-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="208ea-113">Göreli sanal adres (RVA) alandır-statik.</span><span class="sxs-lookup"><span data-stu-id="208ea-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="208ea-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="208ea-114">Requirements</span></span>  
 <span data-ttu-id="208ea-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="208ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208ea-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="208ea-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="208ea-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="208ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="208ea-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208ea-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="208ea-119">See also</span></span>

- [<span data-ttu-id="208ea-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="208ea-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
