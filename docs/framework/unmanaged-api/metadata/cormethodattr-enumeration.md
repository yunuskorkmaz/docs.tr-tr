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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f144426996583d5058f70daed99d8a37cfb6bfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444672"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="cd51c-102">CorMethodAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cd51c-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="cd51c-103">Bir yöntem özelliklerini açıklayan değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd51c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd51c-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="cd51c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cd51c-105">Members</span></span>  
  
|<span data-ttu-id="cd51c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cd51c-106">Member</span></span>|<span data-ttu-id="cd51c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd51c-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="cd51c-108">Üye erişimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="cd51c-109">Üye başvurulamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="cd51c-110">Üye yalnızca üst türü tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="cd51c-111">Üye bu derlemedeki yalnızca alt türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="cd51c-112">Üye accessibly derlemesindeki herkes tarafından olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="cd51c-113">Üye yalnızca türü ve alt türler tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="cd51c-114">Üye türetilen sınıflar ve diğer türleri kendi derlemesi tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="cd51c-115">Üye erişimi olan tüm türleri tarafından kapsama erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="cd51c-116">Üye türü bir parçası olarak yerine bir örneği bir üyesi olarak tanımlandı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="cd51c-117">Yöntemi geçersiz kılınamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="cd51c-118">Yöntem geçersiz kılınabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="cd51c-119">Yöntem adı ve imza yerine yalnızca ada göre gizler belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="cd51c-120">Sanal Tablo düzeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="cd51c-121">Bu yöntemde sanal tablo için kullanılan yuvası yeniden kullanılabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="cd51c-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="cd51c-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="cd51c-123">Yöntem her zaman sanal tablosunda yeni bir yuva alır belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="cd51c-124">Yöntem için görülebilir aynı türlerine göre geçersiz kılınabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="cd51c-125">Yöntem uygulanmadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="cd51c-126">Yöntemi özeldir ve adını açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="cd51c-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="cd51c-127">Yöntem uygulaması PInvoke kullanarak iletilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="cd51c-128">Yöntem yönetilmeyen koda dışarı yönetilen bir yöntem olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="cd51c-129">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="cd51c-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="cd51c-130">Ortak dil çalışma zamanı yöntemi adı kodlama denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="cd51c-131">Yöntemi, kendisiyle ilişkilendirilmiş güvenlik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="cd51c-132">Yöntemi güvenlik kodunu içeren başka bir yöntem çağırır belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd51c-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd51c-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd51c-133">Requirements</span></span>  
 <span data-ttu-id="cd51c-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd51c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd51c-135">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cd51c-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cd51c-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd51c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd51c-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd51c-137">See Also</span></span>  
 [<span data-ttu-id="cd51c-138">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cd51c-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
