---
description: 'Daha fazla bilgi edinin: Corfieldadttr numaralandırması'
title: CorFieldAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: ac342f67a53da75fd9711ebfdd2f2c448cf27d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784502"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="863d3-103">CorFieldAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="863d3-103">CorFieldAttr Enumeration</span></span>

<span data-ttu-id="863d3-104">Bir alanla ilgili meta verileri tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="863d3-104">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="863d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="863d3-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="863d3-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="863d3-106">Members</span></span>  
  
|<span data-ttu-id="863d3-107">Üye</span><span class="sxs-lookup"><span data-stu-id="863d3-107">Member</span></span>|<span data-ttu-id="863d3-108">Description</span><span class="sxs-lookup"><span data-stu-id="863d3-108">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="863d3-109">Erişilebilirlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-109">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="863d3-110">Alana başvurulmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-110">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="863d3-111">Alana yalnızca üst öğe türüyle erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-111">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="863d3-112">Alanı, derlemesinde türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-112">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="863d3-113">Alanı, derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-113">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="863d3-114">Alanına yalnızca türü ve türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-114">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="863d3-115">Alan türetilmiş sınıflar ve kendi derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-115">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="863d3-116">Alana, bu kapsamın görünürlüğünü içeren tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-116">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="863d3-117">Alanın bir örnek üyesi yerine türünün bir üyesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-117">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="863d3-118">Alanın başlatıldıktan sonra değiştirilemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-118">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="863d3-119">Alan değerinin bir derleme zamanı sabiti olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-119">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="863d3-120">Türü uzaktan olduğunda alanın serileştirilmemiş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-120">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="863d3-121">Alanın özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-121">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="863d3-122">Alan uygulamasının PInvoke aracılığıyla iletildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-122">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="863d3-123">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="863d3-123">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="863d3-124">Ortak dil çalışma zamanı meta veri iç API 'Lerinin ad kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-124">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="863d3-125">Alanın sıralama bilgilerini içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-125">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="863d3-126">Alanın varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-126">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="863d3-127">Alanın göreli bir sanal adresi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="863d3-127">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="863d3-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="863d3-128">Requirements</span></span>  

 <span data-ttu-id="863d3-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="863d3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="863d3-130">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="863d3-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="863d3-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="863d3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863d3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="863d3-132">See also</span></span>

- [<span data-ttu-id="863d3-133">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="863d3-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
