---
title: ICLRDataTarget3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54d6535e2b2c4761eb3c67a990c62f2c311cf133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406870"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="df38f-102">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df38f-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="df38f-103">Öğesinin bir alt [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) özel durum bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="df38f-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df38f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df38f-104">Methods</span></span>  
  
|<span data-ttu-id="df38f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df38f-105">Method</span></span>|<span data-ttu-id="df38f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df38f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df38f-107">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df38f-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="df38f-108">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="df38f-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="df38f-109">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df38f-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="df38f-110">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="df38f-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="df38f-111">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df38f-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="df38f-112">Özel durum oluşturdu iş parçacığı kimliği almak için CLR veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="df38f-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df38f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df38f-113">Remarks</span></span>  
 <span data-ttu-id="df38f-114">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="df38f-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="df38f-115">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="df38f-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="df38f-116">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="df38f-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df38f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df38f-117">Requirements</span></span>  
 <span data-ttu-id="df38f-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df38f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df38f-119">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="df38f-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="df38f-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df38f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df38f-121">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df38f-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df38f-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df38f-122">See Also</span></span>  
 [<span data-ttu-id="df38f-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df38f-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="df38f-124">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df38f-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="df38f-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df38f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
