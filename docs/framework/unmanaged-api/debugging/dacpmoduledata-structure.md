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
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860808"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="07cac-102">DacpModuleData Yapısı</span><span class="sxs-lookup"><span data-stu-id="07cac-102">DacpModuleData Structure</span></span>

<span data-ttu-id="07cac-103">Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="07cac-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="07cac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07cac-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="07cac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="07cac-105">Members</span></span>

| <span data-ttu-id="07cac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="07cac-106">Member</span></span>    | <span data-ttu-id="07cac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07cac-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="07cac-108">Modül nesnesinin adresi.</span><span class="sxs-lookup"><span data-stu-id="07cac-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="07cac-109">Taşınabilir çalıştırılabilir (PE) dosyasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07cac-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="07cac-110">Yüklenen görüntünün tabanının adresi.</span><span class="sxs-lookup"><span data-stu-id="07cac-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="07cac-111">Çalışma zamanı tarafından kullanılan ek modül bilgileri için yük arabelleği.</span><span class="sxs-lookup"><span data-stu-id="07cac-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="07cac-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07cac-112">Remarks</span></span>

<span data-ttu-id="07cac-113">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="07cac-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="07cac-114">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="07cac-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="07cac-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07cac-115">Requirements</span></span>
<span data-ttu-id="07cac-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07cac-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="07cac-117">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="07cac-117">**Header:** None</span></span>  
<span data-ttu-id="07cac-118">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="07cac-118">**Library:** None</span></span>  
<span data-ttu-id="07cac-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="07cac-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="07cac-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07cac-120">See also</span></span>

- [<span data-ttu-id="07cac-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="07cac-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="07cac-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="07cac-122">Debugging Structures</span></span>](debugging-structures.md)
