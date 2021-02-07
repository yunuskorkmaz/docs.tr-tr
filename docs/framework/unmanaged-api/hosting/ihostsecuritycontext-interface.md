---
description: 'Daha fazla bilgi edinin: IHostSecurityContext arabirimi'
title: IHostSecurityContext Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: c4c1be00a8b1c9df58797a0f2fc7e60abcab9673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671652"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="0ae0a-103">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ae0a-103">IHostSecurityContext Interface</span></span>

<span data-ttu-id="0ae0a-104">Ortak dil çalışma zamanının (CLR) konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-104">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ae0a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0ae0a-105">Methods</span></span>  
  
|<span data-ttu-id="0ae0a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0ae0a-106">Method</span></span>|<span data-ttu-id="0ae0a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ae0a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ae0a-108">Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ae0a-108">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="0ae0a-109">`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-109">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ae0a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ae0a-110">Remarks</span></span>  

 <span data-ttu-id="0ae0a-111">Bir konak, iş parçacığı belirteçlerine yönelik tüm kod erişimini CLR ve Kullanıcı koduna göre denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-111">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="0ae0a-112">Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-112">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="0ae0a-113">`IHostSecurityContext` çalışma zamanı için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-113">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="0ae0a-114">Çalışma zamanı bu bilgileri kullanarak yakalar `Capture` ve iş parçacığı havuzu çalışan öğesi gönderimi, sonlandırıcısı yürütmesi ve modül ve sınıf oluşturucuları arasında gider.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-114">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ae0a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ae0a-115">Requirements</span></span>  

 <span data-ttu-id="0ae0a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ae0a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae0a-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ae0a-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ae0a-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0ae0a-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ae0a-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae0a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-120">See also</span></span>

- [<span data-ttu-id="0ae0a-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ae0a-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="0ae0a-122">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ae0a-122">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="0ae0a-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ae0a-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
