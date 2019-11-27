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
ms.openlocfilehash: b1586184c91619994ba0dfc9d5dcc277c10f99cf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436450"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="e6606-102">CorTypeAttr Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e6606-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="e6606-103">Tür meta verilerini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e6606-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6606-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6606-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="e6606-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="e6606-105">Members</span></span>  
  
|<span data-ttu-id="e6606-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="e6606-106">Member</span></span>|<span data-ttu-id="e6606-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6606-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="e6606-108">Tür görünürlük bilgileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6606-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="e6606-109">Türün ortak kapsamda değil olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="e6606-110">Türün ortak kapsamda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="e6606-111">Türün genel görünürlük ile iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="e6606-112">Türün özel görünürlük ile iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="e6606-113">Türün aile görünürlüğü ile iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="e6606-114">Türün derleme görünürlüğünde iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="e6606-115">Türün aile ve derleme görünürlüğünde iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="e6606-116">Türün aile veya derleme görünürlüğünde iç içe olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="e6606-117">Türün düzen bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="e6606-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="e6606-118">Bu tür alanların otomatik olarak düzenlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="e6606-119">Bu türdeki alanların sırayla düzenlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="e6606-120">Alan düzeninin açık olarak sağlanmış olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="e6606-121">Tür hakkında anlam bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="e6606-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="e6606-122">Türün bir sınıf olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="e6606-123">Türün bir arabirim olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="e6606-124">Türün soyut olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="e6606-125">Türün uzatılamaz olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="e6606-126">Sınıf adının özel olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-126">Specifies that the class name is special.</span></span> <span data-ttu-id="e6606-127">Adının nasıl yapılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6606-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="e6606-128">Türün içeri aktarılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="e6606-129">Türün seri hale getirilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="e6606-130">Bu türün bir Windows Çalışma Zamanı türü olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="e6606-131">Dizelerin nasıl kodlandığını ve biçimlendirildiğini hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="e6606-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="e6606-132">Bu türün bir LPTSTR öğesini ANSI olarak yorumlaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="e6606-133">Bu türün bir LPTSTR öğesini Unicode olarak yorumlayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="e6606-134">Bu türün bir LPTSTR öğesini otomatik olarak yorumlayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="e6606-135">Türün, `CustomFormatMask`tarafından belirtilen standart olmayan bir kodlamaya sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="e6606-136">Yerel birlikte çalışma için standart olmayan kodlama bilgilerini almak için bu maskeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6606-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="e6606-137">Bu iki bitin değerlerinin anlamı belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="e6606-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="e6606-138">Statik alana ilk erişim denemesinden önce türün başlatılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="e6606-139">Türün verildiğini ve bir tür ileticisi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="e6606-140">Bu bayrak ve aşağıdaki bayraklar ortak dil çalışma zamanı tarafından dahili olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e6606-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="e6606-141">Ortak dil çalışma zamanının ad kodlamasını denetlemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="e6606-142">Türün onunla ilişkili güvenlik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6606-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6606-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6606-143">Requirements</span></span>  
 <span data-ttu-id="e6606-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6606-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6606-145">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e6606-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e6606-146">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6606-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6606-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6606-147">See also</span></span>

- [<span data-ttu-id="e6606-148">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e6606-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
