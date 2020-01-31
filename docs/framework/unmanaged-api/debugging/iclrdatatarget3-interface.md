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
ms.openlocfilehash: f7635dc3fad9b3de30fa052c7d2e67a7e6953fb3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789053"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="33ec6-102">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33ec6-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="33ec6-103">Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="33ec6-103">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33ec6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="33ec6-104">Methods</span></span>  
  
|<span data-ttu-id="33ec6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="33ec6-105">Method</span></span>|<span data-ttu-id="33ec6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33ec6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33ec6-107">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33ec6-107">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="33ec6-108">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="33ec6-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="33ec6-109">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33ec6-109">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="33ec6-110">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="33ec6-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="33ec6-111">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33ec6-111">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="33ec6-112">Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için CLR veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="33ec6-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33ec6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33ec6-113">Remarks</span></span>  
 <span data-ttu-id="33ec6-114">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="33ec6-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="33ec6-115">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="33ec6-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="33ec6-116">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="33ec6-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ec6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33ec6-117">Requirements</span></span>  
 <span data-ttu-id="33ec6-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ec6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ec6-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="33ec6-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="33ec6-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="33ec6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33ec6-121">**.NET Framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="33ec6-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ec6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33ec6-122">See also</span></span>

- [<span data-ttu-id="33ec6-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33ec6-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="33ec6-124">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33ec6-124">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="33ec6-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="33ec6-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
