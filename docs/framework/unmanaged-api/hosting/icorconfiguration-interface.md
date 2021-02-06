---
description: ': ICorConfiguration arabirimi hakkında daha fazla bilgi edinin'
title: ICorConfiguration Arabirimi
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: f75e9e445c7fe4615abcae27756bcc420b5255b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636695"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="8eb7c-103">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-103">ICorConfiguration Interface</span></span>

<span data-ttu-id="8eb7c-104">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-104">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8eb7c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8eb7c-105">Methods</span></span>  
  
|<span data-ttu-id="8eb7c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8eb7c-106">Method</span></span>|<span data-ttu-id="8eb7c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eb7c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8eb7c-108">AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-108">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="8eb7c-109">Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-109">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="8eb7c-110">SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-110">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="8eb7c-111">Hata ayıklama Hizmetleri, CLR iş parçacıkları engellenen ve hata ayıklama için engellenmemiş olarak çağralacak geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-111">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="8eb7c-112">SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-112">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="8eb7c-113">Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-113">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="8eb7c-114">SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-114">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="8eb7c-115">Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-115">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8eb7c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eb7c-116">Requirements</span></span>  

 <span data-ttu-id="8eb7c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb7c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb7c-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8eb7c-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8eb7c-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8eb7c-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8eb7c-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb7c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb7c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb7c-121">See also</span></span>

- [<span data-ttu-id="8eb7c-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8eb7c-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="8eb7c-123">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="8eb7c-123">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
