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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936506"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="06832-102">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="06832-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="06832-103">Uygulama genel derleme önbelleğinde yüklü olduğu bir derlemeye bir uygulama sağlar. bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06832-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06832-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06832-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="06832-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="06832-105">Members</span></span>  
  
|<span data-ttu-id="06832-106">Üye</span><span class="sxs-lookup"><span data-stu-id="06832-106">Member</span></span>|<span data-ttu-id="06832-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06832-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="06832-108">Yapının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="06832-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="06832-109">Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="06832-109">Reserved for future extensibility.</span></span> <span data-ttu-id="06832-110">Bu değer, 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06832-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="06832-111">Varlık başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="06832-111">The entity that adds the reference.</span></span> <span data-ttu-id="06832-112">Bu alan şu değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="06832-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="06832-113">-FUSION_REFCOUNT_MSI_GUID: Derleme, Microsoft Windows Installer kullanarak yüklenen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="06832-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="06832-114">`szIdentifier` Ayarlanmış `MSI`ve `szNonCanonicalData` ayarlanmış `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="06832-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="06832-115">Bu düzen, Windows yan yana derlemeler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06832-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="06832-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Derlemenin görünen bir uygulama tarafından başvurulan **Program Ekle/Kaldır** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="06832-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="06832-117">`szIdentifier` Alan uygulamayla kayıtlarını belirteci sağlar **Program Ekle/Kaldır** arabirimi.</span><span class="sxs-lookup"><span data-stu-id="06832-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="06832-118">-   FUSION_REFCOUNT_FILEPATH_GUID: Derleme, dosya sisteminde dosya tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="06832-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="06832-119">`szIdentifier` Alanı, bu dosyanın yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="06832-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="06832-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Derleme, yalnızca genel olmayan bir dize tarafından temsil edilen bir uygulama tarafından başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="06832-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="06832-121">`szIdentifier` Alanı donuk Bu dize sağlar.</span><span class="sxs-lookup"><span data-stu-id="06832-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="06832-122">Bu değer kaldırdığınızda, Genel Derleme Önbelleği donuk başvuruları varlığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="06832-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="06832-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: Bu değer ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="06832-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="06832-124">Derleme genel derleme önbelleğinde yüklü uygulama tanımlayan benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="06832-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="06832-125">Değerin değerine bağlıdır `guidScheme` alan.</span><span class="sxs-lookup"><span data-stu-id="06832-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="06832-126">Yalnızca başvuru ekler varlık tarafından anlaşılan bir dize.</span><span class="sxs-lookup"><span data-stu-id="06832-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="06832-127">Genel Derleme Önbelleği, bu dizesi depolar, ancak bunları kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="06832-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06832-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06832-128">Requirements</span></span>  
 <span data-ttu-id="06832-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06832-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06832-130">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="06832-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="06832-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06832-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06832-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06832-132">See also</span></span>

- [<span data-ttu-id="06832-133">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="06832-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="06832-134">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="06832-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
