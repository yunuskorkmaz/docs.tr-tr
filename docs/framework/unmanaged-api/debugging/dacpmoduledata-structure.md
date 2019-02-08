---
title: DacpModuleData yapısı
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
ms.openlocfilehash: db3fdaa768e3d1b445f08c3964521570631f0965
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828557"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="fc33f-102">DacpModuleData yapısı</span><span class="sxs-lookup"><span data-stu-id="fc33f-102">DacpModuleData Structure</span></span>

<span data-ttu-id="fc33f-103">Bir modülün çalışma zamanı bilgileri için transport arabellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc33f-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fc33f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc33f-104">Syntax</span></span>

```
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="fc33f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fc33f-105">Members</span></span>

| <span data-ttu-id="fc33f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fc33f-106">Member</span></span>    | <span data-ttu-id="fc33f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc33f-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="fc33f-108">Modülü nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="fc33f-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="fc33f-109">Taşınabilir yürütülebilir (PE) dosyası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc33f-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="fc33f-110">Yüklenen görüntü adresini temel.</span><span class="sxs-lookup"><span data-stu-id="fc33f-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="fc33f-111">Çalışma zamanı tarafından kullanılan modül ek bilgi için yükü arabellek.</span><span class="sxs-lookup"><span data-stu-id="fc33f-111">A payload buffer for additional module information used by the runtime.</span></span> |


## <a name="remarks"></a><span data-ttu-id="fc33f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc33f-112">Remarks</span></span>

<span data-ttu-id="fc33f-113">Bu yapı, çalışma zamanı içinde yer alan ve herhangi bir üst bilgiler veya kitaplık dosyaları gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="fc33f-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="fc33f-114">Bunu kullanmak için yukarıda belirtildiği gibi yapısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc33f-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc33f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc33f-115">Requirements</span></span>
<span data-ttu-id="fc33f-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc33f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fc33f-117">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc33f-117">**Header:** None</span></span>  
<span data-ttu-id="fc33f-118">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc33f-118">**Library:** None</span></span>  
<span data-ttu-id="fc33f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc33f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fc33f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc33f-120">See also</span></span>
- [<span data-ttu-id="fc33f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fc33f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="fc33f-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="fc33f-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
