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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e6521f8013bf92f073ab4b6808871c95ac2802b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700117"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="3380b-102">ICorRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3380b-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="3380b-103">Ortak dil çalışma zamanı (CLR) başlatır.</span><span class="sxs-lookup"><span data-stu-id="3380b-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3380b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3380b-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3380b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3380b-105">Return Value</span></span>  
  
|<span data-ttu-id="3380b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3380b-106">HRESULT</span></span>|<span data-ttu-id="3380b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3380b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3380b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3380b-108">S_OK</span></span>|<span data-ttu-id="3380b-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3380b-109">The operation was successful.</span></span>|  
|<span data-ttu-id="3380b-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3380b-110">S_FALSE</span></span>|<span data-ttu-id="3380b-111">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="3380b-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3380b-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3380b-112">E_FAIL</span></span>|<span data-ttu-id="3380b-113">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3380b-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3380b-114">CLR, artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3380b-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="3380b-115">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3380b-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3380b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3380b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3380b-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3380b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3380b-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3380b-118">Remarks</span></span>  
 <span data-ttu-id="3380b-119">Genellikle çağırmak gerekli değildir `Start` yöntemi, çünkü CLR'nin yönetilen kodu çalıştırmak için ilk istek üzerine otomatik olarak başlar.</span><span class="sxs-lookup"><span data-stu-id="3380b-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3380b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3380b-120">Requirements</span></span>  
 <span data-ttu-id="3380b-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3380b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3380b-122">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3380b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3380b-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3380b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3380b-124">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3380b-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3380b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3380b-125">See also</span></span>

- [<span data-ttu-id="3380b-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3380b-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
