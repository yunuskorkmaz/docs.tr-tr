---
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
ms.openlocfilehash: 4e40f684cc1578672cb8ff474972ce9cdc39efb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718832"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="d09d2-102">CorFieldAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d09d2-102">CorFieldAttr Enumeration</span></span>

<span data-ttu-id="d09d2-103">Bir alanla ilgili meta verileri tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09d2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d09d2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d09d2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d09d2-105">Members</span></span>  
  
|<span data-ttu-id="d09d2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d09d2-106">Member</span></span>|<span data-ttu-id="d09d2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d09d2-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="d09d2-108">Erişilebilirlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="d09d2-109">Alana başvurulmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="d09d2-110">Alana yalnızca üst öğe türüyle erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="d09d2-111">Alanı, derlemesinde türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="d09d2-112">Alanı, derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="d09d2-113">Alanına yalnızca türü ve türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="d09d2-114">Alan türetilmiş sınıflar ve kendi derlemesindeki tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="d09d2-115">Alana, bu kapsamın görünürlüğünü içeren tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="d09d2-116">Alanın bir örnek üyesi yerine türünün bir üyesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="d09d2-117">Alanın başlatıldıktan sonra değiştirilemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="d09d2-118">Alan değerinin bir derleme zamanı sabiti olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="d09d2-119">Türü uzaktan olduğunda alanın serileştirilmemiş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="d09d2-120">Alanın özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="d09d2-121">Alan uygulamasının PInvoke aracılığıyla iletildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="d09d2-122">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d09d2-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="d09d2-123">Ortak dil çalışma zamanı meta veri iç API 'Lerinin ad kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="d09d2-124">Alanın sıralama bilgilerini içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="d09d2-125">Alanın varsayılan bir değere sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="d09d2-126">Alanın göreli bir sanal adresi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09d2-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d09d2-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d09d2-127">Requirements</span></span>  

 <span data-ttu-id="d09d2-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09d2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09d2-129">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d09d2-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d09d2-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09d2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09d2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d09d2-131">See also</span></span>

- [<span data-ttu-id="d09d2-132">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="d09d2-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
