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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b07388b7f7385e93a6ca891e8ea98a2ce69763c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576021"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="6de4d-102">CorFieldAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6de4d-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="6de4d-103">Bir alan hakkında açıklayan meta verileri değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6de4d-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="6de4d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6de4d-105">Members</span></span>  
  
|<span data-ttu-id="6de4d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6de4d-106">Member</span></span>|<span data-ttu-id="6de4d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6de4d-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="6de4d-108">Erişilebilirlik bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="6de4d-109">Alan başvurulamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="6de4d-110">Alan yalnızca kendi üst türü tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="6de4d-111">Alanın kendi derlemedeki türetilmiş sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="6de4d-112">Alanın kendi derlemedeki tüm tür tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="6de4d-113">Alan yalnızca türü tarafından erişilebilir olduğundan ve türetilmiş sınıfları belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="6de4d-114">Alanın kendi derlemesi içindeki tüm türleri ve türetilen sınıflar tarafından erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="6de4d-115">Alanın tüm türleri bu kapsamı tarafından görünürlük ile erişilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="6de4d-116">Alan türünü üyesi yerine bir örnek üyesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="6de4d-117">Alan başlatıldıktan sonra değiştirilemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="6de4d-118">Alan değeri bir derleme zamanı sabiti olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="6de4d-119">Alan türünü düğümlerde olduğunda serileştirildiği değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="6de4d-120">Alan özel olduğundan ve adının açıklayan belirtir nasıl.</span><span class="sxs-lookup"><span data-stu-id="6de4d-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="6de4d-121">Alan uygulamasında PInvoke aracılığıyla iletilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="6de4d-122">İç kullanım için ortak dil çalışma zamanı tarafından ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="6de4d-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="6de4d-123">Ortak dil çalışma zamanı meta veri adı kodlama dahili API'lerde denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="6de4d-124">Alan sıralama bilgilerini içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="6de4d-125">Alanın bir varsayılan değer olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="6de4d-126">Bir göreli sanal adres alanına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6de4d-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6de4d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6de4d-127">Requirements</span></span>  
 <span data-ttu-id="6de4d-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de4d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de4d-129">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6de4d-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6de4d-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de4d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de4d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6de4d-131">See also</span></span>
- [<span data-ttu-id="6de4d-132">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6de4d-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
