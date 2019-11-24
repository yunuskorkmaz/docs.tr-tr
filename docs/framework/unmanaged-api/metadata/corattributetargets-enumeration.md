---
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
ms.openlocfilehash: 5f83cb96e39b257a1d35786130cd5ed31d071de7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443876"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="1bd74-102">CorAttributeTargets Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1bd74-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="1bd74-103">Specifies the application elements on which it is valid to apply an attribute.</span><span class="sxs-lookup"><span data-stu-id="1bd74-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd74-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bd74-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1bd74-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1bd74-105">Members</span></span>  
  
|<span data-ttu-id="1bd74-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1bd74-106">Member</span></span>|<span data-ttu-id="1bd74-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bd74-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="1bd74-108">Attribute can be applied to an assembly.</span><span class="sxs-lookup"><span data-stu-id="1bd74-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="1bd74-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span><span class="sxs-lookup"><span data-stu-id="1bd74-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="1bd74-110">Attribute can be applied to a class.</span><span class="sxs-lookup"><span data-stu-id="1bd74-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="1bd74-111">Attribute can be applied to a structure; that is, a value type.</span><span class="sxs-lookup"><span data-stu-id="1bd74-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="1bd74-112">Attribute can be applied to an enumeration.</span><span class="sxs-lookup"><span data-stu-id="1bd74-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="1bd74-113">Attribute can be applied to a constructor.</span><span class="sxs-lookup"><span data-stu-id="1bd74-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="1bd74-114">Attribute can be applied to a method.</span><span class="sxs-lookup"><span data-stu-id="1bd74-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="1bd74-115">Attribute can be applied to a property.</span><span class="sxs-lookup"><span data-stu-id="1bd74-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="1bd74-116">Attribute can be applied to a field.</span><span class="sxs-lookup"><span data-stu-id="1bd74-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="1bd74-117">Attribute can be applied to an event.</span><span class="sxs-lookup"><span data-stu-id="1bd74-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="1bd74-118">Attribute can be applied to an interface.</span><span class="sxs-lookup"><span data-stu-id="1bd74-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="1bd74-119">Attribute can be applied to a parameter.</span><span class="sxs-lookup"><span data-stu-id="1bd74-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="1bd74-120">Attribute can be applied to a delegate.</span><span class="sxs-lookup"><span data-stu-id="1bd74-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="1bd74-121">Attribute can be applied to a generic parameter.</span><span class="sxs-lookup"><span data-stu-id="1bd74-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="1bd74-122">Attribute can be applied to any application element.</span><span class="sxs-lookup"><span data-stu-id="1bd74-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="1bd74-123">Attribute can be applied to a member of a class.</span><span class="sxs-lookup"><span data-stu-id="1bd74-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd74-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bd74-124">Remarks</span></span>  
 <span data-ttu-id="1bd74-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span><span class="sxs-lookup"><span data-stu-id="1bd74-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="1bd74-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span><span class="sxs-lookup"><span data-stu-id="1bd74-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd74-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bd74-127">Requirements</span></span>  
 <span data-ttu-id="1bd74-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd74-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd74-129">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1bd74-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1bd74-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd74-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd74-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bd74-131">See also</span></span>

- [<span data-ttu-id="1bd74-132">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1bd74-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
