---
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
ms.openlocfilehash: 38042876cf4397418d2e6e6ed2bfbeb2df2d62d8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762298"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="229bb-102">ICorRuntimeHost::CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="229bb-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="229bb-103"><xref:System.AppDomain?displayProperty=nameWithType>Geçerli iş parçacığında yüklü olan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="229bb-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229bb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="229bb-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="229bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="229bb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="229bb-106">dışı <xref:System.AppDomain?displayProperty=nameWithType>İş parçacığının geçerli uygulama etki alanını temsil eden tür işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="229bb-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="229bb-107">Bu işaretçi yazıldığı `IUnknown` için çağıranlar genellikle `QueryInterface` türünde bir işaretçi almak için çağrı çağırmalıdır <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="229bb-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="229bb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="229bb-108">Return Value</span></span>  
  
|<span data-ttu-id="229bb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="229bb-109">HRESULT</span></span>|<span data-ttu-id="229bb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="229bb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="229bb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="229bb-111">S_OK</span></span>|<span data-ttu-id="229bb-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="229bb-112">The operation was successful.</span></span>|  
|<span data-ttu-id="229bb-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="229bb-113">S_FALSE</span></span>|<span data-ttu-id="229bb-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="229bb-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="229bb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="229bb-115">E_FAIL</span></span>|<span data-ttu-id="229bb-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="229bb-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="229bb-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="229bb-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="229bb-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="229bb-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="229bb-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="229bb-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="229bb-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="229bb-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="229bb-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="229bb-121">Requirements</span></span>  
 <span data-ttu-id="229bb-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="229bb-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="229bb-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="229bb-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="229bb-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="229bb-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="229bb-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="229bb-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229bb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="229bb-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="229bb-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="229bb-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
