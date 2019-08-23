---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca51b87e7afc8e9e48d541a32b3bd60a19a5ff70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965964"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="3632a-102">ICorRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3632a-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="3632a-103">Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3632a-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3632a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3632a-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3632a-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3632a-105">Return Value</span></span>  
  
|<span data-ttu-id="3632a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3632a-106">HRESULT</span></span>|<span data-ttu-id="3632a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3632a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3632a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3632a-108">S_OK</span></span>|<span data-ttu-id="3632a-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3632a-109">The operation was successful.</span></span>|  
|<span data-ttu-id="3632a-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3632a-110">S_FALSE</span></span>|<span data-ttu-id="3632a-111">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="3632a-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3632a-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3632a-112">E_FAIL</span></span>|<span data-ttu-id="3632a-113">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3632a-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3632a-114">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3632a-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="3632a-115">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3632a-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3632a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3632a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3632a-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3632a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3632a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3632a-118">Remarks</span></span>  
 <span data-ttu-id="3632a-119">İşlem çıkış sırasında kod yürütmeyi durdurduğundan `Stop` , yöntemi çağırmak genellikle gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="3632a-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3632a-120">Bir çağrısından `Stop`sonra, clr aynı işleme yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="3632a-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3632a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3632a-121">Requirements</span></span>  
 <span data-ttu-id="3632a-122">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3632a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3632a-123">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3632a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3632a-124">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3632a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3632a-125">**.NET Framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3632a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3632a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3632a-126">See also</span></span>

- [<span data-ttu-id="3632a-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3632a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
