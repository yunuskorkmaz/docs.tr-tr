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
ms.openlocfilehash: 2e27082ba4c35bc10eb65139b2af6c81c10d79a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739128"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="47164-102">DacpModuleData Yapısı</span><span class="sxs-lookup"><span data-stu-id="47164-102">DacpModuleData Structure</span></span>

<span data-ttu-id="47164-103">Bir modülün çalışma zamanı bilgileri için transport arabellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47164-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="47164-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47164-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="47164-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="47164-105">Members</span></span>

| <span data-ttu-id="47164-106">Üye</span><span class="sxs-lookup"><span data-stu-id="47164-106">Member</span></span>    | <span data-ttu-id="47164-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47164-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="47164-108">Modülü nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="47164-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="47164-109">Taşınabilir yürütülebilir (PE) dosyası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47164-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="47164-110">Yüklenen görüntü adresini temel.</span><span class="sxs-lookup"><span data-stu-id="47164-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="47164-111">Çalışma zamanı tarafından kullanılan modül ek bilgi için yükü arabellek.</span><span class="sxs-lookup"><span data-stu-id="47164-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="47164-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47164-112">Remarks</span></span>

<span data-ttu-id="47164-113">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="47164-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="47164-114">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47164-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="47164-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47164-115">Requirements</span></span>
<span data-ttu-id="47164-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47164-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="47164-117">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="47164-117">**Header:** None</span></span>  
<span data-ttu-id="47164-118">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="47164-118">**Library:** None</span></span>  
<span data-ttu-id="47164-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="47164-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="47164-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47164-120">See also</span></span>

- [<span data-ttu-id="47164-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="47164-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="47164-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="47164-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
