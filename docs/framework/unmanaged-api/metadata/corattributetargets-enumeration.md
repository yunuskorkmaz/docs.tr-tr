---
description: 'Daha fazla bilgi edinin: CorAttributeTargets numaralandırması'
title: CorAttributeTargets Numaralandırması
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 6f80df31b9da8591fac3d979ede1e9bf0f8ecfc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678504"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="5803d-103">CorAttributeTargets Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5803d-103">CorAttributeTargets Enumeration</span></span>

<span data-ttu-id="5803d-104">Bir öznitelik uygulamak için geçerli olduğu uygulama öğelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5803d-104">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5803d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5803d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="5803d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5803d-106">Members</span></span>  
  
|<span data-ttu-id="5803d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5803d-107">Member</span></span>|<span data-ttu-id="5803d-108">Description</span><span class="sxs-lookup"><span data-stu-id="5803d-108">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="5803d-109">Öznitelik, bir derlemeye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-109">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="5803d-110">Öznitelik, taşınabilir bir çalıştırılabilir (. dll veya. exe) modülüne uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-110">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="5803d-111">Öznitelik, bir sınıfa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-111">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="5803d-112">Öznitelik bir yapıya uygulanabilir; diğer bir deyişle, bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="5803d-112">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="5803d-113">Öznitelik, bir numaralandırmaya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-113">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="5803d-114">Öznitelik, bir oluşturucuya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-114">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="5803d-115">Öznitelik, bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-115">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="5803d-116">Öznitelik, bir özelliğe uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-116">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="5803d-117">Öznitelik, bir alana uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-117">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="5803d-118">Öznitelik, bir olaya uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-118">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="5803d-119">Öznitelik, bir arabirime uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-119">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="5803d-120">Öznitelik, bir parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-120">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="5803d-121">Öznitelik, bir temsilciye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-121">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="5803d-122">Öznitelik, genel parametreye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-122">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="5803d-123">Özniteliği herhangi bir uygulama öğesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-123">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="5803d-124">Öznitelik, bir sınıfın üyesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-124">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5803d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5803d-125">Remarks</span></span>  

 <span data-ttu-id="5803d-126">`CorAttributeTargets`Sabit listesi değerleri, tercih edilen birleşimi almak için bit DÜZEYINDE veya işlemle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5803d-126">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="5803d-127">`CorAttributeTargets`Yönetilen numaralandırmayı paraleller <xref:System.AttributeTargets?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5803d-127">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5803d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5803d-128">Requirements</span></span>  

 <span data-ttu-id="5803d-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5803d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5803d-130">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5803d-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5803d-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5803d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5803d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5803d-132">See also</span></span>

- [<span data-ttu-id="5803d-133">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5803d-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
