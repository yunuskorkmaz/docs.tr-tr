---
title: "EApiCategories Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="8adc6-102">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8adc6-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="8adc6-103">Ana bilgisayar kısmen güvenilen bir kod çalıştırmasını engelleyebilir yeteneklerini kategorileri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8adc6-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8adc6-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="8adc6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8adc6-105">Members</span></span>  
  
|<span data-ttu-id="8adc6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8adc6-106">Member</span></span>|<span data-ttu-id="8adc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8adc6-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="8adc6-108">Tüm sınıflar ve üyeleri tarafından kapsanan yönetilen belirtir `EApiCategories` alanları, kısmen güvenilen kodu çalıştırma engellenir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="8adc6-109">Yönetilen sınıflar ve oluşturma, düzenleme ve dış işlemlere edilmesine izin üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="8adc6-110">Yönetilen sınıflar ve oluşturma, düzenleme ve dış iş parçacıklarını yok etme izin üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="8adc6-111">Yönetilen türler ve iptal bellek sızıntısı üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="8adc6-112">Yönetilen kod kategori yok kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="8adc6-113">Ortak dil çalışma zamanı (CLR) güvenlik altyapısı kısmen güvenilen kod tarafından kullanılan engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="8adc6-114">Yönetilen sınıflar ve üyeleri olan özellikleri barındırılan işlem etkileyebilir kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="8adc6-115">Yönetilen sınıflar ve üyeleri olan özellikleri barındırılan işlemdeki iş parçacıklarının etkileyebilir kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="8adc6-116">Yönetilen sınıflar ve paylaşılan durum kullanıma üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="8adc6-117">Ortak dil çalışma zamanı sınıflar ve kilitleri tutmak kullanıcı kodu izin üyeleri kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="8adc6-118">Yönetilen sınıflar ve izin veren veya insan etkileşimi gerektiren üye kısmen güvenilen kodu çalıştırma engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adc6-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8adc6-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8adc6-119">Remarks</span></span>  
 <span data-ttu-id="8adc6-120">[Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) yöntemi türünde bir parametre alan `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8adc6-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="8adc6-121">`EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili yönetilen için <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8adc6-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8adc6-122">Yönetilen sınıf ile kullanılan <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> numaralandırma, karşılık gelen değerleri doğrudan `EApiCategories` işareti yönetilen türler ve özellikleri tarafından açıklanan kategoriye karşılık gelen açığa üyeleri değerleri, `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="8adc6-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8adc6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8adc6-123">Requirements</span></span>  
 <span data-ttu-id="8adc6-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adc6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adc6-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8adc6-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8adc6-126">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8adc6-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8adc6-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adc6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adc6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8adc6-128">See Also</span></span>  
 [<span data-ttu-id="8adc6-129">Iclrhostprotectionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="8adc6-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="8adc6-130">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8adc6-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
