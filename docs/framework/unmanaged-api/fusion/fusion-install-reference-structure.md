---
description: 'Daha fazla bilgi edinin: FUSION_INSTALL_REFERENCE yapısı'
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
ms.openlocfilehash: 4ac3d2f7d36dd017315a8a3ce6d6185e75f9ddc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761115"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="5b095-103">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="5b095-103">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="5b095-104">Uygulamanın, uygulamanın genel derleme önbelleğinde yüklediği bir derlemeye yaptığı bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b095-104">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b095-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b095-105">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="5b095-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5b095-106">Members</span></span>  
  
|<span data-ttu-id="5b095-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5b095-107">Member</span></span>|<span data-ttu-id="5b095-108">Description</span><span class="sxs-lookup"><span data-stu-id="5b095-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="5b095-109">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5b095-109">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="5b095-110">Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b095-110">Reserved for future extensibility.</span></span> <span data-ttu-id="5b095-111">Bu değer 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b095-111">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="5b095-112">Başvuruyu ekleyen varlık.</span><span class="sxs-lookup"><span data-stu-id="5b095-112">The entity that adds the reference.</span></span> <span data-ttu-id="5b095-113">Bu alan aşağıdaki değerlerden birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="5b095-113">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="5b095-114">-FUSION_REFCOUNT_MSI_GUID: derlemeye, Microsoft Windows Installer kullanılarak yüklenen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="5b095-114">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="5b095-115">`szIdentifier`Alanı olarak ayarlanır `MSI` ve `szNonCanonicalData` alan olarak ayarlanır `Windows Installer` .</span><span class="sxs-lookup"><span data-stu-id="5b095-115">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="5b095-116">Bu düzen Windows yan yana derlemeler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b095-116">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="5b095-117">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: derlemeye **Program Ekle/Kaldır** arabiriminde görünen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="5b095-117">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="5b095-118">`szIdentifier`Alan, uygulamayı **Program Ekle/Kaldır** arabirimiyle kaydeden belirteci sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b095-118">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="5b095-119">-FUSION_REFCOUNT_FILEPATH_GUID: derlemeye dosya sistemindeki bir dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="5b095-119">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="5b095-120">`szIdentifier`Alan, bu dosyanın yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b095-120">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="5b095-121">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: derlemeye yalnızca donuk bir dize tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="5b095-121">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="5b095-122">`szIdentifier`Alan bu donuk dize sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b095-122">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="5b095-123">Genel bütünleştirilmiş kod önbelleği, bu değeri kaldırdığınızda donuk başvuruların varlığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="5b095-123">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="5b095-124">-FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5b095-124">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="5b095-125">Derlemeyi genel derleme önbelleğine yükleyen uygulamayı tanımlayan benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="5b095-125">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="5b095-126">Değeri alanın değerine bağlıdır `guidScheme` .</span><span class="sxs-lookup"><span data-stu-id="5b095-126">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="5b095-127">Yalnızca başvuruyu ekleyen varlık tarafından anlaşılan bir dize.</span><span class="sxs-lookup"><span data-stu-id="5b095-127">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="5b095-128">Genel bütünleştirilmiş kod önbelleği bu dizeyi depolar, ancak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="5b095-128">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b095-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b095-129">Requirements</span></span>  

 <span data-ttu-id="5b095-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b095-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b095-131">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5b095-131">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5b095-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b095-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b095-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b095-133">See also</span></span>

- [<span data-ttu-id="5b095-134">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="5b095-134">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="5b095-135">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="5b095-135">Global Assembly Cache</span></span>](../../app-domains/gac.md)
