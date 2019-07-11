---
title: EApiCategories Numaralandırması
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41513d9b6f98743bfad95e4d9606cfb4927369e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769783"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="ffdc7-102">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ffdc7-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="ffdc7-103">Konak, kısmen güvenilen bir kod çalıştırmasını engelleyebilir özellikleri kategorileri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffdc7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="ffdc7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ffdc7-105">Members</span></span>  
  
|<span data-ttu-id="ffdc7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ffdc7-106">Member</span></span>|<span data-ttu-id="ffdc7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffdc7-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="ffdc7-108">Tüm yönetilen sınıflar ve diğer tarafından kapsanan üyeleri belirtir `EApiCategories` alanlar, kısmen güvenilen bir kod çalıştırmasını engellenir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="ffdc7-109">Yönetilen sınıflar ve oluşturma, düzenleme ve yok edilmesini dış işlemlere izin üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="ffdc7-110">Yönetilen sınıflar ve oluşturma, düzenleme ve dış iş parçacıklarını yok edilmesini sağlayan üyeleri kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="ffdc7-111">Yönetilen türler ve potansiyel olarak iptal bellek dışarıya sızmasına neden olabilecek bir üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="ffdc7-112">Yönetilen kod kategori kısmen güvenilen kod çalıştırılmasının engellenmesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="ffdc7-113">Ortak dil çalışma zamanı (CLR) güvenlik altyapısı kısmen güvenilen kod tarafından kullanılan engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="ffdc7-114">Yönetilen sınıflar ve üyeleri olan yetenekleri barındırılan işlem etkileyebilir kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="ffdc7-115">Yönetilen sınıflar ve üyeleri olan yetenekleri barındırılan işlemdeki iş parçacıkları etkileyebilir kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="ffdc7-116">Yönetilen sınıflar ve paylaşılan durum kullanıma üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="ffdc7-117">Ortak dil çalışma zamanı sınıflar ve kullanıcı kodu için kilitler barındırmıyorsa izin üyeleri kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="ffdc7-118">Yönetilen sınıflar ve izin veren veya insan etkileşimi gerektiren üye kısmen güvenilen bir kod çalıştırmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffdc7-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffdc7-119">Remarks</span></span>  
 <span data-ttu-id="ffdc7-120">[Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi türünde bir parametre alır `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="ffdc7-121">`EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili için yönetilen <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ffdc7-122">Yönetilen sınıf ile kullanılan <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırma değerleri karşılık doğrudan `EApiCategories` yönetilen türleri ve üyeleri tarafından açıklanan kategoriler karşılık gelen özellikleri kullanıma sunan işaretlemek için değerleri `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdc7-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffdc7-123">Requirements</span></span>  
 <span data-ttu-id="ffdc7-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffdc7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdc7-125">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffdc7-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffdc7-126">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffdc7-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffdc7-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdc7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdc7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffdc7-128">See also</span></span>

- [<span data-ttu-id="ffdc7-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffdc7-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="ffdc7-130">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ffdc7-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
