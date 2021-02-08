---
description: 'Daha fazla bilgi edinin: Cormethodadttr numaralandırması'
title: CorMethodAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 4050235675f4b237b184d31378a614a0613ab3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784385"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="b2d23-103">CorMethodAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2d23-103">CorMethodAttr Enumeration</span></span>

<span data-ttu-id="b2d23-104">Bir yöntemin özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-104">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d23-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2d23-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b2d23-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2d23-106">Members</span></span>  
  
|<span data-ttu-id="b2d23-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b2d23-107">Member</span></span>|<span data-ttu-id="b2d23-108">Description</span><span class="sxs-lookup"><span data-stu-id="b2d23-108">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="b2d23-109">Üye erişimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-109">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="b2d23-110">Üyenin başvurumadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-110">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="b2d23-111">Üyenin yalnızca üst tür tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-111">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="b2d23-112">Üyenin yalnızca bu derlemede alt türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-112">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="b2d23-113">Üyenin derlemedeki herkes tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-113">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="b2d23-114">Üyenin yalnızca Type ve alt türleri tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-114">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="b2d23-115">Üyenin türetilmiş sınıflar ve kendi derlemesindeki diğer türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-115">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="b2d23-116">Üyenin kapsama erişimi olan tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-116">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="b2d23-117">Üyenin, bir örneğin üyesi olarak değil türün bir parçası olarak tanımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-117">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="b2d23-118">Yöntemin geçersiz kılınamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-118">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="b2d23-119">Yöntemin geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-119">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="b2d23-120">Yöntemin yalnızca ada göre değil, ad ve imzaya göre gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-120">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="b2d23-121">Sanal tablo yerleşimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-121">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="b2d23-122">Sanal tabloda bu yöntem için kullanılan yuvanın yeniden kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-122">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="b2d23-123">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-123">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="b2d23-124">Yöntemin sanal tabloda her zaman yeni bir yuva aldığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="b2d23-124">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="b2d23-125">Yöntemin görünür olduğu aynı türler tarafından geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-125">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="b2d23-126">Yöntemin uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-126">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="b2d23-127">Yöntemin özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-127">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="b2d23-128">Yöntem uygulamasının PInvoke kullanılarak iletildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-128">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="b2d23-129">Yöntemin yönetilmeyen koda aktarılmış yönetilen bir yöntem olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-129">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="b2d23-130">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b2d23-130">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="b2d23-131">Ortak dil çalışma zamanının Yöntem adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-131">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="b2d23-132">Metodun onunla ilişkili güvenlik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-132">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="b2d23-133">Metodun güvenlik kodu içeren başka bir yöntemi çağırıyorsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2d23-133">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2d23-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2d23-134">Requirements</span></span>  

 <span data-ttu-id="b2d23-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2d23-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2d23-136">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b2d23-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b2d23-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2d23-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d23-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2d23-138">See also</span></span>

- [<span data-ttu-id="b2d23-139">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b2d23-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
