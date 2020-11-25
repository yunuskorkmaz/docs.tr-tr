---
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
ms.openlocfilehash: bc647ad025b5e22187b476383ed0128761cb632f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721042"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="83120-102">ICorRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83120-102">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="83120-103">Ortak dil çalışma zamanını (CLR) başlatır.</span><span class="sxs-lookup"><span data-stu-id="83120-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83120-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="83120-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="83120-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="83120-105">Return Value</span></span>  
  
|<span data-ttu-id="83120-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83120-106">HRESULT</span></span>|<span data-ttu-id="83120-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83120-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83120-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="83120-108">S_OK</span></span>|<span data-ttu-id="83120-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="83120-109">The operation was successful.</span></span>|  
|<span data-ttu-id="83120-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="83120-110">S_FALSE</span></span>|<span data-ttu-id="83120-111">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="83120-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="83120-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83120-112">E_FAIL</span></span>|<span data-ttu-id="83120-113">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="83120-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="83120-114">Bir yöntem E_FAIL döndürürse, CLR artık işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="83120-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="83120-115">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="83120-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="83120-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83120-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83120-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="83120-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83120-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83120-118">Remarks</span></span>  

 <span data-ttu-id="83120-119">Genellikle yöntemi çağırmak gerekmez `Start` , çünkü clr yönetilen kodu çalıştırmak için ilk istekten sonra otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="83120-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83120-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83120-120">Requirements</span></span>  

 <span data-ttu-id="83120-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83120-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83120-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83120-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83120-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="83120-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83120-124">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="83120-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83120-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83120-125">See also</span></span>

- [<span data-ttu-id="83120-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83120-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
