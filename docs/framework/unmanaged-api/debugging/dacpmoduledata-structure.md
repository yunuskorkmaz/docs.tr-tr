---
description: 'Daha fazla bilgi edinin: Davcpmoduledata yapısı'
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
ms.openlocfilehash: 376a49ab78db08e5906e8d33389cdc45fe76e81e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661590"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="da813-103">DacpModuleData Yapısı</span><span class="sxs-lookup"><span data-stu-id="da813-103">DacpModuleData Structure</span></span>

<span data-ttu-id="da813-104">Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da813-104">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="da813-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="da813-105">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="da813-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="da813-106">Members</span></span>

| <span data-ttu-id="da813-107">Üye</span><span class="sxs-lookup"><span data-stu-id="da813-107">Member</span></span>    | <span data-ttu-id="da813-108">Description</span><span class="sxs-lookup"><span data-stu-id="da813-108">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="da813-109">Modül nesnesinin adresi.</span><span class="sxs-lookup"><span data-stu-id="da813-109">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="da813-110">Taşınabilir çalıştırılabilir (PE) dosyasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="da813-110">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="da813-111">Yüklenen görüntünün tabanının adresi.</span><span class="sxs-lookup"><span data-stu-id="da813-111">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="da813-112">Çalışma zamanı tarafından kullanılan ek modül bilgileri için yük arabelleği.</span><span class="sxs-lookup"><span data-stu-id="da813-112">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="da813-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da813-113">Remarks</span></span>

<span data-ttu-id="da813-114">Bu yapı çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="da813-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="da813-115">Kullanmak için, yapıyı yukarıda belirtilen şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="da813-115">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="da813-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da813-116">Requirements</span></span>

<span data-ttu-id="da813-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da813-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="da813-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="da813-118">**Header:** None</span></span>  
<span data-ttu-id="da813-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="da813-119">**Library:** None</span></span>  
<span data-ttu-id="da813-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="da813-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="da813-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da813-121">See also</span></span>

- [<span data-ttu-id="da813-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="da813-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="da813-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="da813-123">Debugging Structures</span></span>](debugging-structures.md)
