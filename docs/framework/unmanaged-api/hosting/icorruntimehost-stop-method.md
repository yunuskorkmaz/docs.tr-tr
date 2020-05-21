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
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762701"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="1bca1-102">ICorRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bca1-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="1bca1-103">Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="1bca1-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bca1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1bca1-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1bca1-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1bca1-105">Return Value</span></span>  
  
|<span data-ttu-id="1bca1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bca1-106">HRESULT</span></span>|<span data-ttu-id="1bca1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bca1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bca1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bca1-108">S_OK</span></span>|<span data-ttu-id="1bca1-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1bca1-109">The operation was successful.</span></span>|  
|<span data-ttu-id="1bca1-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1bca1-110">S_FALSE</span></span>|<span data-ttu-id="1bca1-111">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="1bca1-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1bca1-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bca1-112">E_FAIL</span></span>|<span data-ttu-id="1bca1-113">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1bca1-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1bca1-114">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1bca1-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1bca1-115">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bca1-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1bca1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bca1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bca1-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1bca1-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bca1-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bca1-118">Remarks</span></span>  
 <span data-ttu-id="1bca1-119">`Stop`İşlem çıkış sırasında kod yürütmeyi durdurduğundan, yöntemi çağırmak genellikle gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="1bca1-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bca1-120">Bir çağrısından sonra `Stop` , clr aynı işleme yeniden başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="1bca1-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bca1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bca1-121">Requirements</span></span>  
 <span data-ttu-id="1bca1-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bca1-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bca1-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1bca1-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bca1-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1bca1-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bca1-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1bca1-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bca1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bca1-126">See also</span></span>

- [<span data-ttu-id="1bca1-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bca1-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
