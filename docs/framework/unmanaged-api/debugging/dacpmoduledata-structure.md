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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179196"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="87828-102">DacpModuleData Yapısı</span><span class="sxs-lookup"><span data-stu-id="87828-102">DacpModuleData Structure</span></span>

<span data-ttu-id="87828-103">Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87828-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="87828-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87828-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="87828-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="87828-105">Members</span></span>

| <span data-ttu-id="87828-106">Üye</span><span class="sxs-lookup"><span data-stu-id="87828-106">Member</span></span>    | <span data-ttu-id="87828-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87828-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="87828-108">Modül nesnesinin adresi.</span><span class="sxs-lookup"><span data-stu-id="87828-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="87828-109">Taşınabilir yürütülebilir (PE) dosyasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87828-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="87828-110">Yüklenen görüntütabanının adresi.</span><span class="sxs-lookup"><span data-stu-id="87828-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="87828-111">Çalışma zamanı tarafından kullanılan ek modül bilgileri için bir yük arabelleği.</span><span class="sxs-lookup"><span data-stu-id="87828-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="87828-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87828-112">Remarks</span></span>

<span data-ttu-id="87828-113">Bu yapı çalışma zamanı içinde yaşar ve üstbilgi veya kitaplık dosyaları aracılığıyla açıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="87828-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="87828-114">Kullanmak için, yapıyı yukarıda belirtildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="87828-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="87828-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87828-115">Requirements</span></span>
<span data-ttu-id="87828-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87828-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="87828-117">**Üstbilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="87828-117">**Header:** None</span></span>  
<span data-ttu-id="87828-118">**Kütüphane:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="87828-118">**Library:** None</span></span>  
<span data-ttu-id="87828-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87828-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="87828-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87828-120">See also</span></span>

- [<span data-ttu-id="87828-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="87828-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="87828-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="87828-122">Debugging Structures</span></span>](debugging-structures.md)
