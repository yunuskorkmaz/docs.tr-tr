---
description: ': ICorRuntimeHost:: Stop yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: b44c77b7d0fe3a078efa11756f5fac7ba400ca5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789599"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="abe11-103">ICorRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abe11-103">ICorRuntimeHost::Stop Method</span></span>

<span data-ttu-id="abe11-104">Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="abe11-104">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe11-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="abe11-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="abe11-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="abe11-106">Return Value</span></span>  
  
|<span data-ttu-id="abe11-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abe11-107">HRESULT</span></span>|<span data-ttu-id="abe11-108">Description</span><span class="sxs-lookup"><span data-stu-id="abe11-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abe11-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="abe11-109">S_OK</span></span>|<span data-ttu-id="abe11-110">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="abe11-110">The operation was successful.</span></span>|  
|<span data-ttu-id="abe11-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="abe11-111">S_FALSE</span></span>|<span data-ttu-id="abe11-112">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="abe11-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="abe11-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="abe11-113">E_FAIL</span></span>|<span data-ttu-id="abe11-114">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="abe11-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="abe11-115">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="abe11-115">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="abe11-116">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="abe11-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="abe11-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abe11-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abe11-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="abe11-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abe11-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abe11-119">Remarks</span></span>  

 <span data-ttu-id="abe11-120">`Stop`İşlem çıkış sırasında kod yürütmeyi durdurduğundan, yöntemi çağırmak genellikle gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="abe11-120">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abe11-121">Bir çağrısından sonra `Stop` , clr aynı işleme yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="abe11-121">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe11-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abe11-122">Requirements</span></span>  

 <span data-ttu-id="abe11-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe11-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe11-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="abe11-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abe11-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="abe11-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abe11-126">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="abe11-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe11-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abe11-127">See also</span></span>

- [<span data-ttu-id="abe11-128">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abe11-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
