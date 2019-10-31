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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131210"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="40293-102">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="40293-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="40293-103">Ana bilgisayarın kısmen güvenilen kodda çalışmasını engelleyebilecekleri yetenekler kategorilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="40293-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40293-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40293-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="40293-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="40293-105">Members</span></span>  
  
|<span data-ttu-id="40293-106">Üye</span><span class="sxs-lookup"><span data-stu-id="40293-106">Member</span></span>|<span data-ttu-id="40293-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40293-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="40293-108">Diğer `EApiCategories` alanları kapsamındaki tüm yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="40293-109">Dış işlemlerin oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="40293-110">Dış iş parçacıklarının oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="40293-111">Durdurma sırasında belleği potansiyel olarak sızan yönetilen türlerin ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenebileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="40293-112">Kısmen güvenilen kodda çalıştırmanın hiçbir yönetilen kod kategorisinin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="40293-113">Ortak dil çalışma zamanı (CLR) güvenlik altyapısının kısmen güvenilen kod tarafından kullanılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="40293-114">Özellikleri barındırılan işlemi etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="40293-115">Özellikleri barındırılan işlemdeki iş parçacıklarını etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="40293-116">Paylaşılan durum sergilemiş olan yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="40293-117">Ortak dil çalışma zamanı sınıflarının ve kullanıcı kodunun kilitleri tutmaya izin veren üyelerin kısmen güvenilen kodda çalıştırılmasını engellediği belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="40293-118">İnsan etkileşiminin kısmen güvenilen kodda çalışmasına izin veren veya bunları gerektiren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40293-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40293-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40293-119">Remarks</span></span>  
 <span data-ttu-id="40293-120">[ICLRHostProtectionManager:: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi, `EApiCategories`türünde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="40293-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="40293-121">`EApiCategories` numaralandırması ve `SetProtectedCategories` yöntemi, yönetilen <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfıyla doğrudan ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="40293-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="40293-122">Yönetilen sınıf, `EApiCategories`tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için değerleri doğrudan `EApiCategories` değerlerine karşılık gelen <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırmasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40293-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40293-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40293-123">Requirements</span></span>  
 <span data-ttu-id="40293-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40293-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40293-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40293-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40293-126">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40293-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40293-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40293-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40293-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40293-128">See also</span></span>

- [<span data-ttu-id="40293-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40293-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="40293-130">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="40293-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
