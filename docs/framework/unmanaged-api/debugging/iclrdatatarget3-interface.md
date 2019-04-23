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
ms.openlocfilehash: df113a2839b0f2651e15f4029d86cc5efc171c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111819"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="26ba2-102">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ba2-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="26ba2-103">Öğesinin [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="26ba2-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26ba2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="26ba2-104">Methods</span></span>  
  
|<span data-ttu-id="26ba2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="26ba2-105">Method</span></span>|<span data-ttu-id="26ba2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26ba2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26ba2-107">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ba2-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="26ba2-108">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26ba2-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="26ba2-109">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ba2-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="26ba2-110">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26ba2-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="26ba2-111">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ba2-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="26ba2-112">Özel durum oluşturan iş parçacığı Kimliğini almak için CLR veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26ba2-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26ba2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26ba2-113">Remarks</span></span>  
 <span data-ttu-id="26ba2-114">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="26ba2-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="26ba2-115">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="26ba2-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="26ba2-116">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="26ba2-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26ba2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26ba2-117">Requirements</span></span>  
 <span data-ttu-id="26ba2-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26ba2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26ba2-119">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="26ba2-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="26ba2-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26ba2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26ba2-121">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26ba2-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ba2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26ba2-122">See also</span></span>

- [<span data-ttu-id="26ba2-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ba2-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="26ba2-124">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ba2-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="26ba2-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26ba2-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
