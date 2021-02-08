---
description: ': ICorRuntimeHost:: Start yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::Start Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: d07c0144c7192bc2f57927c294ea472cd6b47f9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789612"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="ed25f-103">ICorRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed25f-103">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="ed25f-104">Ortak dil çalışma zamanını (CLR) başlatır.</span><span class="sxs-lookup"><span data-stu-id="ed25f-104">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed25f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed25f-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ed25f-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed25f-106">Return Value</span></span>  
  
|<span data-ttu-id="ed25f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed25f-107">HRESULT</span></span>|<span data-ttu-id="ed25f-108">Description</span><span class="sxs-lookup"><span data-stu-id="ed25f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed25f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed25f-109">S_OK</span></span>|<span data-ttu-id="ed25f-110">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ed25f-110">The operation was successful.</span></span>|  
|<span data-ttu-id="ed25f-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ed25f-111">S_FALSE</span></span>|<span data-ttu-id="ed25f-112">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="ed25f-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ed25f-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed25f-113">E_FAIL</span></span>|<span data-ttu-id="ed25f-114">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ed25f-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ed25f-115">Bir yöntem E_FAIL döndürürse, CLR artık işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ed25f-115">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="ed25f-116">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed25f-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ed25f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed25f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed25f-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ed25f-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed25f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed25f-119">Remarks</span></span>  

 <span data-ttu-id="ed25f-120">Genellikle yöntemi çağırmak gerekmez `Start` , çünkü clr yönetilen kodu çalıştırmak için ilk istekten sonra otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="ed25f-120">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed25f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed25f-121">Requirements</span></span>  

 <span data-ttu-id="ed25f-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed25f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed25f-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed25f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed25f-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ed25f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed25f-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ed25f-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed25f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed25f-126">See also</span></span>

- [<span data-ttu-id="ed25f-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed25f-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
