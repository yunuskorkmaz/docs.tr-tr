---
title: FUSION_INSTALL_REFERENCE Yapısı
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688815"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="f240e-102">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="f240e-102">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="f240e-103">Uygulamanın, uygulamanın genel derleme önbelleğinde yüklediği bir derlemeye yaptığı bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f240e-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f240e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f240e-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="f240e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f240e-105">Members</span></span>  
  
|<span data-ttu-id="f240e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f240e-106">Member</span></span>|<span data-ttu-id="f240e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f240e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f240e-108">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f240e-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="f240e-109">Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f240e-109">Reserved for future extensibility.</span></span> <span data-ttu-id="f240e-110">Bu değer 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f240e-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="f240e-111">Başvuruyu ekleyen varlık.</span><span class="sxs-lookup"><span data-stu-id="f240e-111">The entity that adds the reference.</span></span> <span data-ttu-id="f240e-112">Bu alan aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="f240e-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="f240e-113">-FUSION_REFCOUNT_MSI_GUID: derlemeye, Microsoft Windows Installer kullanılarak yüklenen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="f240e-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="f240e-114">`szIdentifier`Alanı olarak ayarlanır `MSI` ve `szNonCanonicalData` alan olarak ayarlanır `Windows Installer` .</span><span class="sxs-lookup"><span data-stu-id="f240e-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="f240e-115">Bu düzen Windows yan yana derlemeler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f240e-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="f240e-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: derlemeye **Program Ekle/Kaldır** arabiriminde görünen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="f240e-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="f240e-117">`szIdentifier`Alan, uygulamayı **Program Ekle/Kaldır** arabirimiyle kaydeden belirteci sağlar.</span><span class="sxs-lookup"><span data-stu-id="f240e-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="f240e-118">-FUSION_REFCOUNT_FILEPATH_GUID: derlemeye dosya sistemindeki bir dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="f240e-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="f240e-119">`szIdentifier`Alan, bu dosyanın yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f240e-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="f240e-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: derlemeye yalnızca donuk bir dize tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="f240e-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="f240e-121">`szIdentifier`Alan bu donuk dize sağlar.</span><span class="sxs-lookup"><span data-stu-id="f240e-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="f240e-122">Genel bütünleştirilmiş kod önbelleği, bu değeri kaldırdığınızda donuk başvuruların varlığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="f240e-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="f240e-123">-FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f240e-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="f240e-124">Derlemeyi genel derleme önbelleğine yükleyen uygulamayı tanımlayan benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="f240e-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="f240e-125">Değeri alanın değerine bağlıdır `guidScheme` .</span><span class="sxs-lookup"><span data-stu-id="f240e-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="f240e-126">Yalnızca başvuruyu ekleyen varlık tarafından anlaşılan bir dize.</span><span class="sxs-lookup"><span data-stu-id="f240e-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="f240e-127">Genel bütünleştirilmiş kod önbelleği bu dizeyi depolar, ancak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f240e-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f240e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f240e-128">Requirements</span></span>  

 <span data-ttu-id="f240e-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f240e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f240e-130">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f240e-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f240e-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f240e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f240e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f240e-132">See also</span></span>

- [<span data-ttu-id="f240e-133">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="f240e-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="f240e-134">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="f240e-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
