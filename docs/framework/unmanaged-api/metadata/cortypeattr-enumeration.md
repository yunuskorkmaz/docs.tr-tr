---
title: CorTypeAttr Numaralandırması
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af90055c0a51e61d4032e45d6fa4a4914ddd045f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667943"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="bee5b-102">CorTypeAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bee5b-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="bee5b-103">Türü meta verileri gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bee5b-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="bee5b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bee5b-105">Members</span></span>  
  
|<span data-ttu-id="bee5b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bee5b-106">Member</span></span>|<span data-ttu-id="bee5b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bee5b-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="bee5b-108">Tür görünürlük bilgileri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bee5b-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="bee5b-109">Türün genel kapsam içinde değil belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="bee5b-110">Tür genel kapsamda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="bee5b-111">Türü genel görünürlük ile iç içe belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="bee5b-112">Özel bir görünürlük türü iç içe yerleştirilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="bee5b-113">Tür ailesi görünürlük ile iç içe belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="bee5b-114">Derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="bee5b-115">Aile ve derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="bee5b-116">Aile veya derleme bir görünürlük türü iç içe yerleştirilmiş belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="bee5b-117">Düzen türü bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="bee5b-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="bee5b-118">Bu tür alanlar otomatik olarak düzenlenmiştir belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="bee5b-119">Bu tür alanlar sıralı olarak düzenlenmiştir belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="bee5b-120">Bu alanı düzeni açıkça sağlanan belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="bee5b-121">Anlam türü bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="bee5b-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="bee5b-122">Türün bir sınıf olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="bee5b-123">Türün bir arabirim olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="bee5b-124">Türün Özet olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="bee5b-125">Tür genişletilemez belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="bee5b-126">Sınıf adı özel olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-126">Specifies that the class name is special.</span></span> <span data-ttu-id="bee5b-127">Adını açıklar nasıl.</span><span class="sxs-lookup"><span data-stu-id="bee5b-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="bee5b-128">Tür içe aktarılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="bee5b-129">Türü seri hale getirilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="bee5b-130">Bu tür olduğunu belirten bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="bee5b-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="bee5b-131">Dizeleri nasıl kodlanmış ve biçimlendirilmiş hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="bee5b-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="bee5b-132">Bu tür bir LPTSTR ANSI olarak yorumlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="bee5b-133">Bu tür bir LPTSTR Unicode olarak yorumlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="bee5b-134">Bu tür bir LPTSTR otomatik olarak yorumlar belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="bee5b-135">Türü bir standart kodlama, sahip olduğunu belirtir belirtildiği gibi `CustomFormatMask`.</span><span class="sxs-lookup"><span data-stu-id="bee5b-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="bee5b-136">Yerel birlikte çalışabilirliği için standart kodlama bilgi almak için bu maskesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="bee5b-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="bee5b-137">Bu iki bit değerlerin anlamı, belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="bee5b-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="bee5b-138">Türü statik bir alana erişmek için yapılan ilk girişim önce başlatılmalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="bee5b-139">Türü dışarı belirtir ve bir tür ileticisi.</span><span class="sxs-lookup"><span data-stu-id="bee5b-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="bee5b-140">Bu bayrak ve aşağıdaki bayrakları, ortak dil çalışma zamanı tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bee5b-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="bee5b-141">Ortak dil çalışma zamanı adı kodlama denetleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="bee5b-142">Türü güvenlik ilişkili olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bee5b-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bee5b-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bee5b-143">Requirements</span></span>  
 <span data-ttu-id="bee5b-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee5b-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee5b-145">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bee5b-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bee5b-146">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee5b-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee5b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bee5b-147">See also</span></span>
- [<span data-ttu-id="bee5b-148">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bee5b-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
