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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49784a0eba0458a7b9ddbcd58cbe1a187c3c779a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101222"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="b28ed-102">CorAttributeTargets Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b28ed-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="b28ed-103">Üzerinde bir öznitelik uygulamak için geçerli olduğundan uygulama öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b28ed-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="b28ed-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b28ed-105">Members</span></span>  
  
|<span data-ttu-id="b28ed-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b28ed-106">Member</span></span>|<span data-ttu-id="b28ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28ed-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="b28ed-108">Öznitelik bir bütünleştirilmiş koda uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="b28ed-109">Öznitelik, bir taşınabilir yürütülebilir (.dll veya .exe) modülü için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="b28ed-110">Öznitelik bir sınıfa uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="b28ed-111">Öznitelik, bir yapıya uygulanabilir; diğer bir deyişle, bir değer yazın.</span><span class="sxs-lookup"><span data-stu-id="b28ed-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="b28ed-112">Öznitelik, bir numaralandırma için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="b28ed-113">Öznitelik, bir oluşturucu için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="b28ed-114">Öznitelik, bir yönteme uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="b28ed-115">Öznitelik, bir özellik için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="b28ed-116">Öznitelik, bir alan için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="b28ed-117">Öznitelik, bir olay için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="b28ed-118">Öznitelik, bir arabirim için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="b28ed-119">Öznitelik, bir parametre için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="b28ed-120">Öznitelik, bir temsilci için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="b28ed-121">Genel parametre özniteliği uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="b28ed-122">Öznitelik, herhangi bir uygulama öğeye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="b28ed-123">Öznitelik, bir sınıf üyesine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b28ed-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b28ed-124">Remarks</span></span>  
 <span data-ttu-id="b28ed-125">`CorAttributeTargets` Numaralandırma değerlerinin tercih edilen birleşimi almak için bit düzeyinde bir veya işlem ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b28ed-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="b28ed-126">`CorAttributeTargets` Yönetilen parallels <xref:System.AttributeTargets?displayProperty=nameWithType> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b28ed-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b28ed-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b28ed-127">Requirements</span></span>  
 <span data-ttu-id="b28ed-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b28ed-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b28ed-129">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b28ed-129">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="b28ed-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b28ed-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b28ed-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b28ed-131">See also</span></span>

- [<span data-ttu-id="b28ed-132">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b28ed-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
