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
ms.openlocfilehash: d31b0190ef9a697fb27c849db080bec6c57618ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616391"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="a8fc8-102">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a8fc8-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="a8fc8-103">Ana bilgisayarın kısmen güvenilen kodda çalışmasını engelleyebilecekleri yetenekler kategorilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8fc8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a8fc8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a8fc8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a8fc8-105">Members</span></span>  
  
|<span data-ttu-id="a8fc8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a8fc8-106">Member</span></span>|<span data-ttu-id="a8fc8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8fc8-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="a8fc8-108">Diğer alanlar kapsamındaki tüm yönetilen sınıfların ve üyelerin `EApiCategories` kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="a8fc8-109">Dış işlemlerin oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="a8fc8-110">Dış iş parçacıklarının oluşturulmasına, yönetilmesine ve yok edilmesiyle kısmen güvenilen kodda çalışmasına izin veren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="a8fc8-111">Durdurma sırasında belleği potansiyel olarak sızan yönetilen türlerin ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenebileceği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="a8fc8-112">Kısmen güvenilen kodda çalıştırmanın hiçbir yönetilen kod kategorisinin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="a8fc8-113">Ortak dil çalışma zamanı (CLR) güvenlik altyapısının kısmen güvenilen kod tarafından kullanılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="a8fc8-114">Özellikleri barındırılan işlemi etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="a8fc8-115">Özellikleri barındırılan işlemdeki iş parçacıklarını etkileyebilecek yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="a8fc8-116">Paylaşılan durum sergilemiş olan yönetilen sınıfların ve üyelerin kısmen güvenilen kodda çalıştırılmasını engellenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="a8fc8-117">Ortak dil çalışma zamanı sınıflarının ve kullanıcı kodunun kilitleri tutmaya izin veren üyelerin kısmen güvenilen kodda çalıştırılmasını engellediği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="a8fc8-118">İnsan etkileşiminin kısmen güvenilen kodda çalışmasına izin veren veya bunları gerektiren yönetilen sınıfların ve üyelerin engellenip engellenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8fc8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8fc8-119">Remarks</span></span>  
 <span data-ttu-id="a8fc8-120">[ICLRHostProtectionManager:: SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi türünde bir parametre alır `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="a8fc8-120">The [ICLRHostProtectionManager::SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="a8fc8-121">`EApiCategories`Sabit listesi ve `SetProtectedCategories` yöntemi doğrudan yönetilen <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a8fc8-122">Yönetilen sınıf, <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> `EApiCategories` tarafından açıklanan kategorilere karşılık gelen özellikleri açığa çıkaran yönetilen türleri ve üyeleri işaretlemek için değerleri doğrudan değerlere karşılık gelen numaralandırmada kullanılır `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="a8fc8-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8fc8-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8fc8-123">Requirements</span></span>  
 <span data-ttu-id="a8fc8-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8fc8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8fc8-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8fc8-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8fc8-126">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8fc8-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8fc8-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8fc8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fc8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-128">See also</span></span>

- [<span data-ttu-id="a8fc8-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8fc8-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="a8fc8-130">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a8fc8-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
