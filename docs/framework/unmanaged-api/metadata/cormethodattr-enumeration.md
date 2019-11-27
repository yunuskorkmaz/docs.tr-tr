---
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
ms.openlocfilehash: 74088d1cd018bb07406fc7d00ff83d783a98b663
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450233"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="359e3-102">CorMethodAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="359e3-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="359e3-103">Bir yöntemin özelliklerini tanımlayan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="359e3-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="359e3-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="359e3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="359e3-105">Members</span></span>  
  
|<span data-ttu-id="359e3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="359e3-106">Member</span></span>|<span data-ttu-id="359e3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="359e3-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="359e3-108">Üye erişimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="359e3-109">Üyenin başvurumadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="359e3-110">Üyenin yalnızca üst tür tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="359e3-111">Üyenin yalnızca bu derlemede alt türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="359e3-112">Üyenin derlemedeki herkes tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="359e3-113">Üyenin yalnızca Type ve alt türleri tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="359e3-114">Üyenin türetilmiş sınıflar ve kendi derlemesindeki diğer türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="359e3-115">Üyenin kapsama erişimi olan tüm türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="359e3-116">Üyenin, bir örneğin üyesi olarak değil türün bir parçası olarak tanımlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="359e3-117">Yöntemin geçersiz kılınamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="359e3-118">Yöntemin geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="359e3-119">Yöntemin yalnızca ada göre değil, ad ve imzaya göre gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="359e3-120">Sanal tablo yerleşimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="359e3-121">Sanal tabloda bu yöntem için kullanılan yuvanın yeniden kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="359e3-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="359e3-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="359e3-123">Yöntemin sanal tabloda her zaman yeni bir yuva aldığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="359e3-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="359e3-124">Yöntemin görünür olduğu aynı türler tarafından geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="359e3-125">Yöntemin uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="359e3-126">Yöntemin özel olduğunu ve adının nasıl kullanıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="359e3-127">Yöntem uygulamasının PInvoke kullanılarak iletildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="359e3-128">Yöntemin yönetilmeyen koda aktarılmış yönetilen bir yöntem olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="359e3-129">Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="359e3-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="359e3-130">Ortak dil çalışma zamanının Yöntem adının kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="359e3-131">Metodun onunla ilişkili güvenlik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="359e3-132">Metodun güvenlik kodu içeren başka bir yöntemi çağırıyorsa belirtir.</span><span class="sxs-lookup"><span data-stu-id="359e3-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="359e3-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="359e3-133">Requirements</span></span>  
 <span data-ttu-id="359e3-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359e3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359e3-135">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="359e3-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="359e3-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359e3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359e3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="359e3-137">See also</span></span>

- [<span data-ttu-id="359e3-138">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="359e3-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
