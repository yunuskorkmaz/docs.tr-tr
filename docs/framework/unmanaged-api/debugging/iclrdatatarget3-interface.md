---
description: 'Daha fazla bilgi edinin: ICLRDataTarget3 Interface'
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
ms.openlocfilehash: deea609298563e60897f9bedab9fb1e175dc7b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794796"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="289cf-103">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="289cf-103">ICLRDataTarget3 Interface</span></span>

<span data-ttu-id="289cf-104">Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="289cf-104">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="289cf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="289cf-105">Methods</span></span>  
  
|<span data-ttu-id="289cf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="289cf-106">Method</span></span>|<span data-ttu-id="289cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="289cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="289cf-108">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="289cf-108">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="289cf-109">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="289cf-109">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="289cf-110">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="289cf-110">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="289cf-111">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="289cf-111">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="289cf-112">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="289cf-112">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="289cf-113">Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için CLR veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="289cf-113">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="289cf-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="289cf-114">Remarks</span></span>  

 <span data-ttu-id="289cf-115">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="289cf-115">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="289cf-116">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="289cf-116">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="289cf-117">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="289cf-117">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289cf-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="289cf-118">Requirements</span></span>  

 <span data-ttu-id="289cf-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289cf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289cf-120">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="289cf-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="289cf-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="289cf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="289cf-122">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="289cf-122">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289cf-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="289cf-123">See also</span></span>

- [<span data-ttu-id="289cf-124">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="289cf-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="289cf-125">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="289cf-125">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="289cf-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="289cf-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
