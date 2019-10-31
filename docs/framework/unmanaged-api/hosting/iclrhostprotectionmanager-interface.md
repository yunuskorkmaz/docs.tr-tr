---
title: ICLRHostProtectionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 0487a87420c888cf5466f54c28c2d89623260add
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141054"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="c9f81-102">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9f81-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="c9f81-103">Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9f81-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9f81-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9f81-104">Methods</span></span>  
  
|<span data-ttu-id="c9f81-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c9f81-105">Method</span></span>|<span data-ttu-id="c9f81-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9f81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9f81-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="c9f81-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="c9f81-108">Önemli ortak dil çalışma zamanı (CLR) hatalarına neden olabilecek nadir bazı yarış durumlarının hiçbir şekilde ortaya çıkması garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9f81-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="c9f81-109">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9f81-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="c9f81-110">Kısmen güvenilen kodda çalışması engellenecek olan yönetilen türlerin ve üyelerin kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9f81-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9f81-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9f81-111">Requirements</span></span>  
 <span data-ttu-id="c9f81-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f81-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f81-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9f81-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9f81-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c9f81-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9f81-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f81-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9f81-116">See also</span></span>

- [<span data-ttu-id="c9f81-117">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9f81-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="c9f81-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9f81-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
