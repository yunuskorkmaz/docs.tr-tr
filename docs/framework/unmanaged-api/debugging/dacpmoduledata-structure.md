---
title: DacpModuleData Yapısı
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 752d87c5f4a6b8d854a06be8962ee754cdd4622d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132015"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="e2f5b-102">DacpModuleData Yapısı</span><span class="sxs-lookup"><span data-stu-id="e2f5b-102">DacpModuleData Structure</span></span>

<span data-ttu-id="e2f5b-103">Bir modülün çalışma zamanı bilgileri için transport arabellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e2f5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2f5b-104">Syntax</span></span>

```
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="e2f5b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e2f5b-105">Members</span></span>

| <span data-ttu-id="e2f5b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e2f5b-106">Member</span></span>    | <span data-ttu-id="e2f5b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2f5b-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="e2f5b-108">Modülü nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="e2f5b-109">Taşınabilir yürütülebilir (PE) dosyası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="e2f5b-110">Yüklenen görüntü adresini temel.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="e2f5b-111">Çalışma zamanı tarafından kullanılan modül ek bilgi için yükü arabellek.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e2f5b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2f5b-112">Remarks</span></span>

<span data-ttu-id="e2f5b-113">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e2f5b-114">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2f5b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2f5b-115">Requirements</span></span>
<span data-ttu-id="e2f5b-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f5b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e2f5b-117">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-117">**Header:** None</span></span>  
<span data-ttu-id="e2f5b-118">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="e2f5b-118">**Library:** None</span></span>  
<span data-ttu-id="e2f5b-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f5b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e2f5b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-120">See also</span></span>

- [<span data-ttu-id="e2f5b-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e2f5b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e2f5b-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e2f5b-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
