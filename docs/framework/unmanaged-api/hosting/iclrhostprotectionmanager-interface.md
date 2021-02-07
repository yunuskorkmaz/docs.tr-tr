---
description: ': ICLRHostProtectionManager Arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689254"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="2045b-103">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2045b-103">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="2045b-104">Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2045b-104">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2045b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2045b-105">Methods</span></span>  
  
|<span data-ttu-id="2045b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2045b-106">Method</span></span>|<span data-ttu-id="2045b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2045b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2045b-108">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="2045b-108">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="2045b-109">Önemli ortak dil çalışma zamanı (CLR) hatalarına neden olabilecek nadir bazı yarış durumlarının hiçbir şekilde ortaya çıkması garantisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2045b-109">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="2045b-110">SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2045b-110">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="2045b-111">Kısmen güvenilen kodda çalışması engellenecek olan yönetilen türlerin ve üyelerin kategorilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2045b-111">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2045b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2045b-112">Requirements</span></span>  

 <span data-ttu-id="2045b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2045b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2045b-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2045b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2045b-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2045b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2045b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2045b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2045b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2045b-117">See also</span></span>

- [<span data-ttu-id="2045b-118">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2045b-118">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="2045b-119">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2045b-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
