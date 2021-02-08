---
description: ': ICorRuntimeHost:: CurrentDomain Yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::CurrentDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: fd75028b57475a620cc88a75016911dd0ab55b2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784905"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="21756-103">ICorRuntimeHost::CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21756-103">ICorRuntimeHost::CurrentDomain Method</span></span>

<span data-ttu-id="21756-104"><xref:System.AppDomain?displayProperty=nameWithType>Geçerli iş parçacığında yüklü olan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="21756-104">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21756-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21756-105">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21756-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21756-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="21756-107">dışı <xref:System.AppDomain?displayProperty=nameWithType> İş parçacığının geçerli uygulama etki alanını temsil eden tür işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="21756-107">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="21756-108">Bu işaretçi yazıldığı `IUnknown` için çağıranlar genellikle `QueryInterface` türünde bir işaretçi almak için çağrı çağırmalıdır <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="21756-108">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21756-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21756-109">Return Value</span></span>  
  
|<span data-ttu-id="21756-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21756-110">HRESULT</span></span>|<span data-ttu-id="21756-111">Description</span><span class="sxs-lookup"><span data-stu-id="21756-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21756-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="21756-112">S_OK</span></span>|<span data-ttu-id="21756-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="21756-113">The operation was successful.</span></span>|  
|<span data-ttu-id="21756-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="21756-114">S_FALSE</span></span>|<span data-ttu-id="21756-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="21756-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="21756-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21756-116">E_FAIL</span></span>|<span data-ttu-id="21756-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="21756-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="21756-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21756-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="21756-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="21756-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21756-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21756-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21756-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="21756-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21756-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21756-122">Requirements</span></span>  

 <span data-ttu-id="21756-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21756-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21756-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21756-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21756-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="21756-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21756-126">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="21756-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21756-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21756-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="21756-128">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21756-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
